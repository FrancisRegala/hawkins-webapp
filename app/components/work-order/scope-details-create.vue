<script setup lang="ts">
    const emit = defineEmits(['dataReady']);

    defineExpose({
        sendDataToParentNow, // Expose the function itself
    });

    const activeScope = ref(['0'])
    const scopeDetails = ref([{
        id: 1,
        icon: 'i-lucide-box',
        label: 'Scope Details',
        content: {
            CallType: '',
            WorkScope: '',
            BillToARCustomer: '',
            CustomerPO: '',
            PriorityName: '',
            IsTrackingWIP: '',
            PriceMethod: '',
            UseAgreementRates: '',
            IsPreventativeMaintenance: '',
            RevenueRecognition: '',
            RateTemplate: '',
            Description: '',
            Notes: '',
        }
    }])

    function sendDataToParentNow() {
        emit('dataReady', scopeDetails.value);
        console.log("ChildDataSender: 'dataReady' event emitted with:", scopeDetails);
    }
</script>

<template>
    <UAccordion v-model="activeScope" type="multiple" :items="scopeDetails">
        <template #body="{ item }">
            <div class="grid grid-cols-1 md:grid-cols-3 xl:grid-cols-4 gap-2">
                <div class="pb-4">
                    <UFormField
                        name="CallType"
                        label="Call Type:"
                    >
                        <UInput
                            v-model="item.content.CallType"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="WorkScope"
                        label="Work Scope:"
                    >
                        <UInput
                            v-model="item.content.WorkScope"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="BillToARCustomer"
                        label="Bill to AR Customer:"
                    >
                        <UInput
                            v-model="item.content.BillToARCustomer"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="CustomerPO"
                        label="Customer PO:"
                    >
                        <UInput
                            v-model="item.content.CustomerPO"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="PriorityName"
                        label="Priority Name:"
                    >
                        <UInput
                            v-model="item.content.PriorityName"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="IsTrackingWIP"
                        label="Is Tracking WIP?:"
                    >
                        <UInput
                            v-model="item.content.IsTrackingWIP"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="PriceMethod"
                        label="Price Method:"
                    >
                        <UInput
                            v-model="item.content.PriceMethod"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="UseAgreementRates"
                        label="Use Agreement Rates:"
                    >
                        <UInput
                            v-model="item.content.UseAgreementRates"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="IsPreventativeMaintenance"
                        label="Is Preventative Maintenance?:"
                    >
                        <UInput
                            v-model="item.content.IsPreventativeMaintenance"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="RevenueRecognition"
                        label="Revenue Recognition:"
                    >
                        <UInput
                            v-model="item.content.RevenueRecognition"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4">
                    <UFormField
                        name="RateTemplate"
                        label="Rate Template:"
                    >
                        <UInput
                            v-model="item.content.RateTemplate"
                            autocomplete="off"
                            variant="subtle"
                        />
                    </UFormField>
                </div>
                <div class="pb-4 pr-4 col-span-2 w-full">
                    <UFormField
                        name="Description"
                        label="Description:"
                    >
                        <UTextarea
                            v-model="item.content.Description"
                            autocomplete="off"
                            variant="subtle"
                            class="w-full"
                        />
                    </UFormField>
                </div>
                <div class="pb-4 pr-4 col-span-2 w-full">
                    <UFormField
                        name="Notes"
                        label="Notes:"
                    >
                        <UTextarea
                            v-model="item.content.Notes"
                            autocomplete="off"
                            variant="subtle"
                            class="w-full"
                        />
                    </UFormField>
                </div>
            </div>
        </template>
    </UAccordion>
</template>
