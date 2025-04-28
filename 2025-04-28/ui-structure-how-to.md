# 🛠️ Special Session Report – How to Modify the UI Structure (Dropdowns, Inputs, Layouts)

**Date**: 2025-04-21  
**Purpose**: Provide a reusable reference for how to modify and expand the frontend UI structure in the Frogpad.AI ecosystem, especially for adding new input fields like dropdowns, text areas, or categories.

---

## ✅ UI Tech Stack Summary

Your UI is built using:

- **React (TypeScript)**
- **TailwindCSS** for all styling
- **shadcn/ui** component library
- Path aliasing via `@/` structure
- Functional component structure (e.g., `ResearchForm.tsx`, `Index.tsx`)

---

## 🔧 How to Add a Dropdown to the UI Form

Edit: `src/components/ResearchForm.tsx`

### Step 1: Define Options

Above your form component:

```ts
const categoryOptions = [
  { label: "Legal", value: "legal" },
  { label: "Finance", value: "finance" },
  { label: "Technology", value: "technology" }
];
```

### Step 2: Add Dropdown Using `shadcn/ui`

Inside the form JSX:

```tsx
<FormField
  control={form.control}
  name="category"
  render={({ field }) => (
    <FormItem>
      <FormLabel>Category</FormLabel>
      <Select onValueChange={field.onChange} defaultValue={field.value}>
        <FormControl>
          <SelectTrigger>
            <SelectValue placeholder="Select a category" />
          </SelectTrigger>
        </FormControl>
        <SelectContent>
          {categoryOptions.map((option) => (
            <SelectItem key={option.value} value={option.value}>
              {option.label}
            </SelectItem>
          ))}
        </SelectContent>
      </Select>
      <FormMessage />
    </FormItem>
  )}
/>
```

---

## 🧠 Notes

- Every new field should also be defined in your form schema:
  ```ts
  const form = useForm<FormValues>({
    defaultValues: {
      searchTerm: "",
      category: ""
    }
  });
  ```
- Adjust the `handleSubmit()` logic in `Index.tsx` to send `category` as part of the payload.

---

## 💡 Other Components You Can Add

- `<Textarea>`: for longform questions or instructions
- `<Checkbox>`: for toggles like “Include citations”
- `<RadioGroup>`: for mutually exclusive options

---

## 🧠 Memory Reset Recovery Note

> Use `ResearchForm.tsx` to define new fields with shadcn/ui and Tailwind utility classes. Update your form schema and `handleSubmit` logic in `Index.tsx` to handle new data fields in queries.
