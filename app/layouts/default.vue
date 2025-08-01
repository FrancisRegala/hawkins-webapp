<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()
const toast = useToast()

const open = ref(false)

const links = [[{
  label: 'Home',
  icon: 'i-lucide-house',
  to: '/',
  onSelect: () => {
    open.value = false
  }
},
{
  label: 'Work Order',
  icon: 'i-material-symbols-lists',
  to: '/work-order/',
  onSelect: () => {
    open.value = false
  }
},
{
  label: 'Quotation',
  icon: 'i-lucide-circle-dollar-sign',
  to: '/quotation/',
  onSelect: () => {
    open.value = false
  }
}
// ,{
//   label: 'Settings',
//   to: '/settings',
//   icon: 'i-lucide-settings',
//   defaultOpen: true,
//   type: 'trigger',
//   children: [{
//     label: 'General',
//     to: '/settings',
//     exact: true,
//     onSelect: () => {
//       open.value = false
//     }
//   }, {
//     label: 'Members',
//     to: '/settings/members',
//     onSelect: () => {
//       open.value = false
//     }
//   }, {
//     label: 'Notifications',
//     to: '/settings/notifications',
//     onSelect: () => {
//       open.value = false
//     }
//   }, {
//     label: 'Security',
//     to: '/settings/security',
//     onSelect: () => {
//       open.value = false
//     }
//   }]
// }],
// [{
//   label: 'Feedback',
//   icon: 'i-lucide-message-circle',
//   to: 'https://github.com/nuxt-ui-pro/dashboard',
//   target: '_blank'
// }, {
//   label: 'Help & Support',
//   icon: 'i-lucide-info',
//   to: 'https://github.com/nuxt/ui-pro',
//   target: '_blank'
// }
],[
    {
      label: 'Material',
      icon: 'i-lucide-settings',
      to: '/material',
      onSelect: () => {
        open.value = false
      }
    },
    // {
    //   label: 'Inbox',
    //   icon: 'i-lucide-inbox',
    //   to: '/inbox',
    //   badge: '4',
    //   onSelect: () => {
    //     open.value = false
    //   }
    // }
]] satisfies NavigationMenuItem[][]

const groups = computed(() => [{
  id: 'links',
  label: 'Go to',
  items: links.flat()
}, {
  id: 'code',
  label: 'Code',
  items: [{
    id: 'source',
    label: 'View page source',
    icon: 'i-simple-icons-github',
    to: `https://github.com/nuxt-ui-pro/dashboard/blob/main/app/pages${route.path === '/' ? '/index' : route.path}.vue`,
    target: '_blank'
  }]
}])

onMounted(async () => {
  const cookie = useCookie('cookie-consent')
  if (cookie.value === 'accepted') {
    return
  }

  // toast.add({
  //   title: 'We use first-party cookies to enhance your experience on our website.',
  //   duration: 0,
  //   close: false,
  //   actions: [{
  //     label: 'Accept',
  //     color: 'neutral',
  //     variant: 'outline',
  //     onClick: () => {
  //       cookie.value = 'accepted'
  //     }
  //   }, {
  //     label: 'Opt out',
  //     color: 'neutral',
  //     variant: 'ghost'
  //   }]
  // })
})
</script>

<template>
  <UDashboardGroup unit="rem">
    <UDashboardSidebar
      id="default"
      v-model:open="open"
      collapsible
      resizable
      class="bg-elevated/25"
      :ui="{ footer: 'lg:border-t lg:border-default' }"
    >
      <template #header="{ collapsed }">
        <TeamsMenu :collapsed="collapsed" />
      </template>

      <template #default="{ collapsed }">
        <UDashboardSearchButton :collapsed="collapsed" class="bg-transparent ring-default" />

        <UNavigationMenu
          :collapsed="collapsed"
          :items="links[0]"
          orientation="vertical"
          tooltip
          popover
          class="border-b border-default"
        />

        <UNavigationMenu
          :collapsed="collapsed"
          :items="links[1]"
          orientation="vertical"
          tooltip
          class=""
        />
      </template>

      <template #footer="{ collapsed }">
        <UserMenu :collapsed="collapsed" />
      </template>
    </UDashboardSidebar>

    <UDashboardSearch :groups="groups" />

    <slot />

    <NotificationsSlideover />
  </UDashboardGroup>
</template>
