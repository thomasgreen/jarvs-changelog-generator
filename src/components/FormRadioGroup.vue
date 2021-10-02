<template>
    <RadioGroup v-model="selected" class="mt-1 sm:mt-0 sm:col-span-2 max-w-lg">
        <div class="bg-white rounded-md -space-y-px">
            <RadioGroupOption
                as="template"
                v-for="(option, optionIdx) in options"
                :key="option.label"
                :value="option"
                v-slot="{ checked, active }"
            >
                <div
                    :class="[
                        optionIdx === 0 ? 'rounded-tl-md rounded-tr-md' : '',
                        optionIdx === options.length - 1
                            ? 'rounded-bl-md rounded-br-md'
                            : '',
                        checked
                            ? 'bg-primary-alt text-primary z-10'
                            : 'border-gray-200',
                        'relative border p-4 flex cursor-pointer focus:outline-none',
                    ]"
                >
                    <span
                        :class="[
                            checked
                                ? 'bg-primary border-transparent'
                                : 'bg-white border-gray-300',
                            active
                                ? 'ring-2 ring-offset-2 ring-primary'
                                : '',
                            'h-4 w-4 mt-0.5 mr-3 cursor-pointer rounded-full border flex  flex-none items-center justify-center',
                        ]"
                        aria-hidden="true"
                    >
                        <span class="rounded-full bg-white w-1.5 h-1.5" />
                    </span>
                    <div class="flex flex-col">
                        <RadioGroupLabel
                            as="span"
                            :class="[
                                checked ? 'text-primary' : 'text-gray-900',
                                'block text-sm font-medium',
                            ]"
                        >
                            {{ option.label }}
                        </RadioGroupLabel>
                        <RadioGroupDescription
                            as="span"
                            :class="[
                                checked ? 'text-primary' : 'text-gray-500',
                                'block text-sm',
                            ]"
                        >
                            {{ option.description }}
                        </RadioGroupDescription>
                    </div>
                </div>
            </RadioGroupOption>
        </div>
    </RadioGroup>
</template>

<script>
import { ref, watch } from "vue";
import {
    RadioGroup,
    RadioGroupDescription,
    RadioGroupLabel,
    RadioGroupOption,
} from "@headlessui/vue";

export default {
    emits: ["update:modelValue"],
    components: {
        RadioGroup,
        RadioGroupDescription,
        RadioGroupLabel,
        RadioGroupOption,
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
