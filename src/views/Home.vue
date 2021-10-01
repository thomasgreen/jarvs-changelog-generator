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

                        <div class="sm:col-span-3">
                            <FormLabel for="description_type">
                                Description Type
                            </FormLabel>

                            <div class="mt-1">
                                <select
                                    id="description_type"
                                    name="description_type"
                                    autocomplete="description_type"
                                    v-model="formData.description_type"
                                    class="
                                        shadow-sm
                                        focus:ring-indigo-500
                                        focus:border-indigo-500
                                        block
                                        w-full
                                        sm:text-sm
                                        border-gray-300
                                        rounded-md
                                    "
                                >
                                    <option>internal</option>
                                    <option>addition</option>
                                    <option>bug</option>
                                </select>
                            </div>
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
                        <div class="sm:col-span-4">
                            <div>
                                <legend
                                    class="text-base font-medium text-gray-900"
                                >
                                    cdesecurity
                                </legend>
                            </div>
                            <div class="mt-4 space-y-4">
                                <div class="flex items-center">
                                    <input
                                        id="cdesecurity-not-impacted"
                                        name="cdesecurity"
                                        v-model="formData.cdesecurity"
                                        value="not impacted"
                                        type="radio"
                                        checked
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="cdesecurity-not-impacted"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Not Impacted
                                    </label>
                                </div>
                                <div class="flex items-center">
                                    <input
                                        id="cdesecurity-impacted"
                                        name="cdesecurity"
                                        v-model="formData.cdesecurity"
                                        value="impacted"
                                        type="radio"
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="cdesecurity-impacted"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Impacted
                                    </label>
                                </div>
                            </div>
                        </div>

                        <div class="sm:col-span-4">
                            <div>
                                <legend
                                    class="text-base font-medium text-gray-900"
                                >
                                    privacy
                                </legend>
                            </div>
                            <div class="mt-4 space-y-4">
                                <div class="flex items-center">
                                    <input
                                        id="privacy-not-impacted"
                                        name="privacy"
                                        v-model="formData.privacy"
                                        value="not impacted"
                                        type="radio"
                                        checked
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="privacy-not-impacted"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Not Impacted
                                    </label>
                                </div>
                                <div class="flex items-center">
                                    <input
                                        id="privacy-impacted"
                                        name="privacy"
                                        v-model="formData.privacy"
                                        value="impacted"
                                        type="radio"
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="privacy-impacted"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Impacted
                                    </label>
                                </div>
                            </div>
                        </div>

                        <div class="sm:col-span-4">
                            <div>
                                <legend
                                    class="text-base font-medium text-gray-900"
                                >
                                    complexity
                                </legend>
                            </div>
                            <div class="mt-4 space-y-4">
                                <div class="flex items-center">
                                    <input
                                        id="complexity-simple"
                                        name="complexity"
                                        v-model="formData.complexity"
                                        value="simple"
                                        type="radio"
                                        checked
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="complexity-simple"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Simple
                                    </label>
                                </div>
                                <div class="flex items-center">
                                    <input
                                        id="complexity-complex"
                                        name="complexity"
                                        v-model="formData.complexity"
                                        value="complex"
                                        type="radio"
                                        class="
                                            focus:ring-indigo-500
                                            h-4
                                            w-4
                                            text-indigo-600
                                            border-gray-300
                                        "
                                    />
                                    <label
                                        for="complexity-complex"
                                        class="
                                            ml-3
                                            block
                                            text-sm
                                            font-medium
                                            text-gray-700
                                        "
                                    >
                                        Complex
                                    </label>
                                </div>
                            </div>
                        </div>

                        <div class="sm:col-span-4">
                            <FormLabel for="release_priority">
                                Release Priority
                            </FormLabel>

                            <div class="mt-1">
                                <select
                                    id="release_priority"
                                    name="release_priority"
                                    autocomplete="release_priority"
                                    v-model="formData.release_priority"
                                    class="
                                        shadow-sm
                                        focus:ring-indigo-500
                                        focus:border-indigo-500
                                        block
                                        w-full
                                        sm:text-sm
                                        border-gray-300
                                        rounded-md
                                    "
                                >
                                    <option>p1</option>
                                    <option>p2</option>
                                    <option>p3</option>
                                </select>
                            </div>
                        </div>

                        <div class="sm:col-span-3">
                            <FormLabel for="device_type">
                                Device Type
                            </FormLabel>

                            <div class="mt-1">
                                <select
                                    id="device_type"
                                    name="device_type"
                                    v-model="formData.device_type"
                                    autocomplete="device_type"
                                    class="
                                        shadow-sm
                                        focus:ring-indigo-500
                                        focus:border-indigo-500
                                        block
                                        w-full
                                        sm:text-sm
                                        border-gray-300
                                        rounded-md
                                    "
                                >
                                    <option>all</option>
                                    <option>mobile</option>
                                    <option>tablet</option>
                                    <option>desktop</option>
                                    <option>cli</option>
                                </select>
                            </div>
                        </div>

                        <div class="sm:col-span-3">
                            <FormLabel for="site_type"> Site Type </FormLabel>

                            <div class="mt-1">
                                <select
                                    id="site_type"
                                    name="site_type"
                                    v-model="formData.site_type"
                                    autocomplete="site_type"
                                    class="
                                        shadow-sm
                                        focus:ring-indigo-500
                                        focus:border-indigo-500
                                        block
                                        w-full
                                        sm:text-sm
                                        border-gray-300
                                        rounded-md
                                    "
                                >
                                    <option>all</option>
                                    <option>responsive</option>
                                    <option>user_first</option>
                                </select>
                            </div>
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
                            <div class="mt-1">
                                <input
                                    id="team"
                                    name="team"
                                    v-model="formData.team"
                                    type="text"
                                    autocomplete="module"
                                    class="
                                        shadow-sm
                                        focus:ring-indigo-500
                                        focus:border-indigo-500
                                        block
                                        w-full
                                        sm:text-sm
                                        border-gray-300
                                        rounded-md
                                    "
                                />
                            </div>
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
                description: "text",
                link: "",
                description_type: "internal",
                site_type: "all",
                release_priority: "p3",
                cdesecurity: "not impacted",
                privacy: "not impacted",
                complexity: "simple",
                team: "optimisation",
                device_type: "all",
                module: "core",
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
