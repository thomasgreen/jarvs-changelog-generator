<template>
  <div>
    <form
      class="space-y-8 divide-y divide-gray-200 max-w-3xl mx-auto"
      @submit.prevent="submitted"
    >
      <div class="space-y-8 divide-y divide-gray-200 sm:space-y-5">
        <div>
          <FormSectionHeader title="Description">
            Please provide a description of the changes made in your Pull
            Request.
          </FormSectionHeader>

          <FormInputGroup>
            <FormInputWrapper>
              <FormLabel for="description">
                Description
              </FormLabel>

              <FormTextArea
                v-model="formData.description"
                name="description"
                required
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="description_type">
                Description Type
              </FormLabel>

              <FormRadioGroup
                id="description_type"
                v-model="formData.description_type"
                :options="options.description_type"
                :selected-key="formData.description_type"
              />
            </FormInputWrapper>
          </FormInputGroup>
        </div>

        <div>
          <FormSectionHeader title="Link & Module">
            Please provide what page and module have been affected.
          </FormSectionHeader>

          <FormInputGroup>
            <FormInputWrapper>
              <FormLabel for="link">
                Link
              </FormLabel>
              <FormInputText
                v-model="formData.link"
                name="link"
                required
                autocomplete="link"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="link">
                Ticket
              </FormLabel>
              <FormInputText
                v-model="formData.ticket"
                name="ticket"
                type="number"
                autocomplete="ticket"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="module">
                Module
              </FormLabel>

              <FormInputText
                v-model="formData.module"
                name="module"
                required
                autocomplete="module"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="device_type">
                Device Type
              </FormLabel>

              <FormInputSelect
                id="device_type"
                v-model="formData.device_type"
                :options="options.device_type"
                :selected-key="formData.device_type"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="site_type">
                Site Type
              </FormLabel>

              <FormInputSelect
                id="site_type"
                v-model="formData.site_type"
                :options="options.site_type"
                :selected-key="formData.site_type"
              />
            </FormInputWrapper>
          </FormInputGroup>
        </div>

        <div>
          <FormSectionHeader title="Team">
            Select your engineering team.
          </FormSectionHeader>

          <FormInputGroup>
            <FormInputWrapper>
              <FormLabel for="team">
                Team
              </FormLabel>

              <FormInputSelect
                v-model="formData.team"
                :options="options.team"
                :selected-key="formData.team"
              />
            </FormInputWrapper>
          </FormInputGroup>
        </div>

        <div>
          <FormSectionHeader title="Platform Impact">
            Please select if the platform is impacted in a way that requires
            further reviw.
          </FormSectionHeader>

          <FormInputGroup>
            <FormInputWrapper>
              <FormLabel for="cdesecurity">
                CDE Security
              </FormLabel>

              <FormRadioGroup
                id="cdesecurity"
                v-model="formData.cdesecurity"
                :options="options.impacted"
                :selected-key="formData.cdesecurity"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="privacy">
                Privacy
              </FormLabel>

              <FormRadioGroup
                id="privacy"
                v-model="formData.privacy"
                :options="options.impacted"
                :selected-key="formData.privacy"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="complexity">
                Complexity
              </FormLabel>

              <FormRadioGroup
                id="complexity"
                v-model="formData.complexity"
                :options="options.complexity"
                :selected-key="formData.complexity"
              />
            </FormInputWrapper>

            <FormInputWrapper>
              <FormLabel for="cacheclearrequired">
                Cache Clear Required?
              </FormLabel>

              <FormRadioGroup
                id="cacheclearrequired"
                v-model="formData.cacheclearrequired"
                :options="options.cacheclearrequired"
                :selected-key="formData.cacheclearrequired"
              />
            </FormInputWrapper>
          </FormInputGroup>
        </div>

        <div>
          <FormInputGroup>
            <FormSectionHeader title="Release Priortiy">
              This should be used so, at a glance, someone can see how important
              this change is.
            </FormSectionHeader>

            <FormInputWrapper>
              <FormLabel for="complexity">
                Release Priority
              </FormLabel>

              <FormRadioGroup
                id="complexity"
                v-model="formData.release_priority"
                :options="options.priority"
                :selected-key="formData.release_priority"
              />
            </FormInputWrapper>
          </FormInputGroup>
        </div>
      </div>

      <div class="pt-5">
        <div class="flex justify-end">
          <button
            type="submit"
            class="ml-3 inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-primary hover:bg-primary focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary"
          >
            Generate Changelog
          </button>
        </div>
      </div>
    </form>

    <TransitionRoot
      appear
      :show="isOpen"
      as="template"
    >
      <Dialog
        as="div"
        @close="closeModal"
      >
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
                class="inline-block w-full max-w-md p-6 my-8 overflow-hidden text-left align-middle transition-all bg-white shadow-xl rounded-2xl"
              >
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900"
                >
                  Succesfully Copied to Clipboard
                </DialogTitle>
                <div class="mt-2">
                  <pre
                    class="text-sm text-gray-500 white-space-pre-wrap"
                    v-html="renderedOutput"
                  />
                </div>

                <div class="mt-4">
                  <button
                    type="button"
                    class="inline-flex justify-center px-4 py-2 text-sm font-medium text-primary bg-primary-alt border border-transparent rounded-md hover:bg-primary-alt focus:outline-none focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:ring-primary"
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
import FormRadioGroup from "../components/FormRadioGroup.vue";
import FormInputSelect from "../components/FormInputSelect.vue";
import FormSectionHeader from "../components/FormSectionHeader.vue";
import FormInputGroup from "../components/FormInputGroup.vue";
import FormInputWrapper from "../components/FormInputWrapper.vue";

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
    FormSectionHeader,
    FormInputGroup,
    FormInputWrapper,
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
        ticket: "",
        site_type: "all",
        release_priority: this.$route.query.priority || "p3",
        cdesecurity: "not impacted",
        privacy: "not impacted",
        complexity: "simple",
        team: this.$route.query.team || "optimisation",
        device_type: "all",
        module: "core",
        cacheclearrequired: "no",
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
        cacheclearrequired: [
          {
            id: "yes",
            label: "Yes",
          },
          {
            id: "no",
            label: "No",
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
          {
            id: "other",
            label: "Other",
          },
        ],
        description_type: [
          {
            id: "addition",
            label: "Addition",
            description:
              "If your change adds new functionality. This will be public by default.",
          },
          {
            id: "bug",
            label: "Bug",
            description: "For a change that fixes an OSD, Fatal Error etc.",
          },
          {
            id: "internal",
            label: "Internal",
            description: "For Changes that have no impact on clients.",
          },
          {
            id: "issue",
            label: "Issue",
            description:
              "Something that isn't working as expected such as a broken link or unstyled element. This will be public by default.",
          },
          {
            id: "update",
            label: "Update",
            description:
              "If your change updates existing functionality. This will be public by default.",
          },
        ],
        team: [
          {
            id: "api",
            label: "API Team",
          },
          {
            id: "architects",
            label: "Architects",
          },
          {
            id: "checkout",
            label: "Checkout Team",
          },
          {
            id: "client_features",
            label: "Client Features",
          },
          {
            id: "core_product",
            label: "Core Product",
          },
          {
            id: "customer_ar",
            label: "Customer AR Team",
          },
          {
            id: "dependencies",
            label: "Dependencies",
          },
          {
            id: "devops",
            label: "DevOps",
          },
          {
            id: "epos",
            label: "EPOS team",
          },
          {
            id: "mobile_app",
            label: "Mobile App Team",
          },
          {
            id: "multi_channel",
            label: "Multi Channel Team",
          },
          {
            id: "optimisation",
            label: "Optimisation Team",
          },
          {
            id: "partnerships",
            label: "Partnerships",
          },
          {
            id: "payments",
            label: "Payments",
          },
          {
            id: "platform",
            label: "Platform",
          },
          {
            id: "pm_build",
            label: "PM Build",
          },
          {
            id: "pm_testing",
            label: "PM Testing",
          },
          {
            id: "product_discovery",
            label: "Product Discovery Team",
          },
          {
            id: "projects",
            label: "Projects",
          },
          {
            id: "value_added",
            label: "Value Added",
          },
        ],
      },
    };
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

        if (value === "") {
          continue;
        }

        string += "@" + key + " " + value + "\n";
      }
      return string;
    },
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
