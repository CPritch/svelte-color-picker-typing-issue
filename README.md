# Svelte Awesome Color Picker Typing Issue

Repro of Svelte Awesome Color Picker pnpm workspace monorepo typing issue.

The typing error is as follows:

```
Type '{ wrapper: Component<Props, {}, "wrapper">; }' is not assignable to type 'Partial<Components>'.
  Types of property 'wrapper' are incompatible.
    Type 'import("svelte").Component<import("C:/Users/ceepr/Dev/svelte-color-picker-typing-issue/node_modules/.pnpm/svelte-awesome-color-picker@4.0.1_svelte@5.28.2/node_modules/svelte-awesome-color-picker/dist/components/variant/chrome-picker/Wrapper.svelte").Props, {}, "wrapper">' is not assignable to type 'import("svelte").Component<Props, {}, "wrapper">'.
      Types of parameters 'props' and 'props' are incompatible.
        Type 'Props' is not assignable to type 'import("C:/Users/ceepr/Dev/svelte-color-picker-typing-issue/node_modules/.pnpm/svelte-awesome-color-picker@4.0.1_svelte@5.28.2/node_modules/svelte-awesome-color-picker/dist/components/variant/chrome-picker/Wrapper.svelte").Props'.
          Types of property 'wrapper' are incompatible.
            Type 'HTMLElement | undefined' is not assignable to type 'HTMLElement'.
              Type 'undefined' is not assignable to type 'HTMLElement'.ts(2322)

```

## Steps to Reproduce

1. Clone the repo: `git clone https://github.com/CPritch/svelte-color-picker-typing-issue`
2. Install packages using pnpm `pnpm i`
3. Ovbserve the error at `/site/src/routes/+page.svelte`

## Cause of Issue

The types are inferred from usage in the root of the library, this leads to ColorPicker.components to require specific file identifiers rather than their types. This causes a type conflict when using pnpm workspaces.