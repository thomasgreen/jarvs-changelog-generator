<template>
    <div class="mt-1 sm:mt-0 sm:col-span-2 max-w-lg">
        <Listbox v-model="selected">
            <div class="relative mt-1">
                <ListboxButton
                    class="
                        relative
                        w-full
                        py-2
                        pl-3
                        pr-10
                        text-left
                        bg-white
                        rounded-lg
                        shadow-md
                        cursor-default
                        focus:outline-none
                        focus-visible:ring-2
                        focus-visible:ring-opacity-75
                        focus-visible:ring-white
                        focus-visible:ring-offset-orange-300
                        focus-visible:ring-offset-2
                        focus-visible:border-indigo-500
                        sm:text-sm
                    "
                >
                    <span class="block truncate">{{
                        selected.label
                    }}</span>
                    <span
                        class="
                            absolute
                            inset-y-0
                            right-0
                            flex
                            items-center
                            pr-2
                            pointer-events-none
                        "
                    >
                        <SelectorIcon
                            class="w-5 h-5 text-gray-400"
                            aria-hidden="true"
                        />
                    </span>
                </ListboxButton>

                <transition
                    leave-active-class="transition duration-100 ease-in"
                    leave-from-class="opacity-100"
                    leave-to-class="opacity-0"
                >
                    <ListboxOptions
                        class="
                            absolute
                            w-full
                            py-1
                            mt-1
                            overflow-auto
                            text-base
                            bg-white
                            rounded-md
                            shadow-lg
                            max-h-60
                            ring-1 ring-black ring-opacity-5
                            focus:outline-none
                            sm:text-sm
                        "
                    >
                        <ListboxOption
                            v-slot="{ active, selected }"
                            v-for="option in options"
                            :key="option.id"
                            :value="option"
                            as="template"
                        >
                            <li
                                :class="[
                                    active
                                        ? 'text-indigo-900 bg-indigo-100'
                                        : 'text-gray-900',
                                    'cursor-default select-none relative py-2 pl-10 pr-4',
                                ]"
                            >
                                <span
                                    :class="[
                                        selected
                                            ? 'font-medium'
                                            : 'font-normal',
                                        'block truncate',
                                    ]"
                                    >{{ option.label }}</span
                                >
                                <span
                                    v-if="selected"
                                    class="
                                        absolute
                                        inset-y-0
                                        left-0
                                        flex
                                        items-center
                                        pl-3
                                        text-amber-600
                                    "
                                >
                                    <CheckIcon
                                        class="w-5 h-5"
                                        aria-hidden="true"
                                    />
                                </span>
                            </li>
                        </ListboxOption>
                    </ListboxOptions>
                </transition>
            </div>
        </Listbox>
    </div>
</template>

<script>
import { ref, watch } from "vue";
import {
    Listbox,
    ListboxLabel,
    ListboxButton,
    ListboxOptions,
    ListboxOption,
} from "@headlessui/vue";
import { CheckIcon, SelectorIcon } from "@heroicons/vue/solid";

export default {
    emits: ["update:modelValue"],

    components: {
        Listbox,
        ListboxLabel,
        ListboxButton,
        ListboxOptions,
        ListboxOption,
        CheckIcon,
        SelectorIcon,
    },
props: {
        options: {
            type: Object,
            required: true,
        },
        selectedKey: {
            type: [Number, String],
            required: false,
        },
        modelValue: { type: String },
    },
    setup(props, { emit }) {
        const options = props.options;

        const selectedKey = options.findIndex((x) => x.id === props.selectedKey);

        let selected = ref(options[selectedKey]);

        watch(selected, (newValue, oldValue) => {
            emit("update:modelValue", newValue.id);
        });

        return {
            options,
            selected,
        };
    },
};
</script>
