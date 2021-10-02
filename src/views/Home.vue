<template>
    <div class="max-w-3xl mx-auto">
        <form
            class="space-y-8 divide-y divide-gray-200"
            @submit.prevent="submitted"
        >
            <div class="space-y-8 divide-y divide-gray-200">
                <div>
                    <div>
                        <h3 class="text-lg leading-6 font-medium text-gray-900">
                            Description
                        </h3>
                    </div>
                    <div
                        class="
                            mt-6
                            grid grid-cols-1
                            gap-y-6 gap-x-4
                            sm:grid-cols-6
                        "
                    >
                        <div class="sm:col-span-6">
                            <FormLabel for="description">
                                Description
                            </FormLabel>

                            <FormTextArea
                                name="description"
                                v-model="formData.description"
                                required
                            />
                        </div>

                        <div class="sm:col-span-6">
                            <FormLabel for="description_type">
                                Description Type
                            </FormLabel>

                            <FormRadioGroup
                                id="description_type"
                                v-model="formData.description_type"
                                :options="options.description_type"
                                :selectedKey="formData.description_type"
                            />
                        </div>
                    </div>
                </div>

                <div class="pt-8">
                    <div>
                        <h3 class="text-lg leading-6 font-medium text-gray-900">
                            Changes Information
                        </h3>
                    </div>
                    <div
                        class="
                            mt-6
                            grid grid-cols-2
                            gap-y-6 gap-x-4
                            sm:grid-cols-6
                        "
                    >
                        <div class="sm:col-span-6">
                            <FormLabel for="cdesecurity">
                                CDE Security
                            </FormLabel>

                            <FormRadioGroup
                                id="cdesecurity"
                                v-model="formData.cdesecurity"
                                :options="options.impacted"
                                :selectedKey="formData.cdesecurity"
                            />
                        </div>

                        <div class="sm:col-span-6">
                            <FormLabel for="privacy"> Privacy </FormLabel>

                            <FormRadioGroup
                                id="privacy"
                                v-model="formData.privacy"
                                :options="options.impacted"
                                :selectedKey="formData.privacy"
                            />
                        </div>

                        <div class="sm:col-span-6">
                            <FormLabel for="complexity"> Complexity </FormLabel>

                            <FormRadioGroup
                                id="complexity"
                                v-model="formData.complexity"
                                :options="options.complexity"
                                :selectedKey="formData.complexity"
                            />
                        </div>

                        <div class="sm:col-span-6">
                            <FormLabel for="complexity">
                                Release Priority
                            </FormLabel>

                            <FormRadioGroup
                                id="complexity"
                                v-model="formData.release_priority"
                                :options="options.priority"
                                :selectedKey="formData.release_priority"
                            />
                        </div>

                        <div class="sm:col-span-3">
                            <FormLabel for="device_type">
                                Device Type
                            </FormLabel>

                            <FormInputSelect
                                id="device_type"
                                v-model="formData.device_type"
                                :options="options.device_type"
                                :selectedKey="formData.device_type"
                            />
                        </div>
                        <div class="sm:col-span-3">
                            <FormLabel for="site_type"> Site Type </FormLabel>

                            <FormInputSelect
                                id="site_type"
                                v-model="formData.site_type"
                                :options="options.site_type"
                                :selectedKey="formData.site_type"
                            />
                        </div>

                        <div class="sm:col-span-4">
                            <FormLabel for="link"> Link </FormLabel>
                            <FormInputText
                                name="link"
                                v-model="formData.link"
                                required
                                autocomplete="link"
                            />
                        </div>

                        <div class="sm:col-span-4">
                            <FormLabel for="module"> Module </FormLabel>

                            <FormInputText
                                name="module"
                                v-model="formData.module"
                                required
                                autocomplete="module"
                            />
                        </div>

                        <div class="sm:col-span-4">
                            <FormLabel for="team"> Team </FormLabel>

                            <FormInputSelect
                                v-model="formData.team"
                                :options="options.team"
                                :selectedKey="formData.team"
                            />
                        </div>
                    </div>
                </div>
            </div>

            <div class="pt-5">
                <div class="flex justify-end">
                    <button
                        type="submit"
                        class="
                            ml-3
                            inline-flex
                            justify-center
                            py-2
                            px-4
                            border border-transparent
                            shadow-sm
                            text-sm
                            font-medium
                            rounded-md
                            text-white
                            bg-indigo-600
                            hover:bg-indigo-700
                            focus:outline-none
                            focus:ring-2
                            focus:ring-offset-2
                            focus:ring-indigo-500
                        "
                    >
                        Save
                    </button>
                </div>
            </div>
        </form>

        <TransitionRoot appear :show="isOpen" as="template">
            <Dialog as="div" @close="closeModal">
                <div class="fixed inset-0 z-10 overflow-y-auto">
                    <div class="min-h-screen px-4 text-center">
                        <TransitionChild
                            as="template"
                            enter="duration-300 ease-out"
                            enter-from="opacity-0"
                            enter-to="opacity-100"
                            leave="duration-200 ease-in"
                            leave-from="opacity-100"
                            leave-to="opacity-0"
                        >
                            <DialogOverlay class="fixed inset-0" />
                        </TransitionChild>

                        <span
                            class="inline-block h-screen align-middle"
                            aria-hidden="true"
                        >
                            &#8203;
                        </span>

                        <TransitionChild
                            as="template"
                            enter="duration-300 ease-out"
                            enter-from="opacity-0 scale-95"
                            enter-to="opacity-100 scale-100"
                            leave="duration-200 ease-in"
                            leave-from="opacity-100 scale-100"
                            leave-to="opacity-0 scale-95"
                        >
                            <div
                                class="
                                    inline-block
                                    w-full
                                    max-w-md
                                    p-6
                                    my-8
                                    overflow-hidden
                                    text-left
                                    align-middle
                                    transition-all
                                    transform
                                    bg-white
                                    shadow-xl
                                    rounded-2xl
                                "
                            >
                                <DialogTitle
                                    as="h3"
                                    class="
                                        text-lg
                                        font-medium
                                        leading-6
                                        text-gray-900
                                    "
                                >
                                    Succesfully Copied to Clipboard
                                </DialogTitle>
                                <div class="mt-2">
                                    <pre
                                        class="
                                            text-sm text-gray-500
                                            white-space-pre-wrap
                                        "
                                        v-html="renderedOutput"
                                    />
                                </div>

                                <div class="mt-4">
                                    <button
                                        type="button"
                                        class="
                                            inline-flex
                                            justify-center
                                            px-4
                                            py-2
                                            text-sm
                                            font-medium
                                            text-blue-900
                                            bg-blue-100
                                            border border-transparent
                                            rounded-md
                                            hover:bg-blue-200
                                            focus:outline-none
                                            focus-visible:ring-2
                                            focus-visible:ring-offset-2
                                            focus-visible:ring-blue-500
                                        "
                                        @click="closeModal"
                                    >
                                        Got it, thanks!
                                    </button>
                                </div>
                            </div>
                        </TransitionChild>
                    </div>
                </div>
            </Dialog>
        </TransitionRoot>
    </div>
</template>

<script>
import { ref } from "vue";
import {
    TransitionRoot,
    TransitionChild,
    Dialog,
    DialogOverlay,
    DialogTitle,
} from "@headlessui/vue";

import FormLabel from "../components/FormLabel.vue";
import FormTextArea from "../components/FormTextArea.vue";
import FormInputText from "../components/FormInputText.vue";
import FormRadioGroup from "../components/FormRadioGroup.vue";
import FormInputSelect from "../components/FormInputSelect.vue";

export default {
    components: {
        TransitionRoot,
        TransitionChild,
        Dialog,
        DialogOverlay,
        DialogTitle,
        FormLabel,
        FormTextArea,
        FormInputText,
        FormRadioGroup,
        FormInputSelect,
    },
    computed: {
        renderedOutput() {
            let string =
                "@" +
                this.formData.description_type +
                " " +
                this.formData.description +
                "\n";

            for (const [key, value] of Object.entries(this.formData)) {
                if (key === "description_type" || key === "description") {
                    continue;
                }

                string += "@" + key + " " + value + "\n";
            }
            return string;
        },
    },
    data() {
        return {
            is_submitted: false,
            isOpen: false,
            output: "",
            formData: {
                description: "",
                link: "",
                description_type: "internal",
                site_type: "all",
                release_priority: "p3",
                cdesecurity: "not impacted",
                privacy: "not impacted",
                complexity: "simple",
                team: this.$route.query.team || "optimisation",
                device_type: "all",
                module: "core",
            },
            options: {
                impacted: [
                    {
                        id: "not impacted",
                        label: "Not Impacted",
                    },
                    {
                        id: "impacted",
                        label: "Impacted",
                    },
                ],
                complexity: [
                    {
                        id: "simple",
                        label: "Simple",
                    },
                    {
                        id: "complex",
                        label: "Complex",
                    },
                ],
                site_type: [
                    {
                        id: "all",
                        label: "All",
                    },
                    {
                        id: "responsive",
                        label: "Responsive",
                    },
                    {
                        id: "user_first",
                        label: "User First",
                    },
                ],
                priority: [
                    {
                        id: "p1",
                        label: "P1",
                    },
                    {
                        id: "p2",
                        label: "P2",
                    },
                    {
                        id: "p3",
                        label: "P3",
                    },
                ],
                device_type: [
                    {
                        id: "all",
                        label: "All",
                    },
                    {
                        id: "desktop",
                        label: "Desktop",
                    },
                    {
                        id: "mobile",
                        label: "Mobile",
                    },
                    {
                        id: "tablet",
                        label: "Tablet",
                    },
                    {
                        id: "cli",
                        label: "CLI",
                    },
                ],
                description_type: [
                    {
                        id: "internal",
                        label: "Internal",
                        description: "lorem ipsum delorem est",
                    },
                    {
                        id: "addition",
                        label: "Addition",
                        description: "random string goes here",
                    },
                ],
                team: [
                    {
                        id: "optimisation",
                        label: "Optimisation Team",
                    },
                    {
                        id: "projects",
                        label: "Projects",
                    },
                    {
                        id: "systems_engineering",
                        label: "Systems Engineering",
                    },
                ],
            },
        };
    },
    methods: {
        submitted() {
            this.is_submitted = true;
            this.$copyText(this.renderedOutput);
            this.openModal();
        },
        closeModal() {
            this.isOpen = false;
        },
        openModal() {
            this.isOpen = true;
        },
    },
};
</script>
