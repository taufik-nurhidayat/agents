Spacing must from parent element
```tsx
// correct sample
<main className="space-y-4">
  <section>...</section>
  <section>...</section>
</main>
```

```tsx
// wrong sample
<main>
  <section className="mb-4">...</section>
  <section className="mt-4">...</section>
</main>
```
