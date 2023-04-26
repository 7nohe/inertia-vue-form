# Inertia Vue Form

> Validation Form Helper Library for Inertia and Vue

## Installation

```
$ npm install @inertia-vue-form/zod
```

## Usage

```vue
<script setup lang="ts">
import { useZodForm } from '@inertia-vue-form/zod';
import { z } from 'zod';

const schema = z.object({
  name: z.string().max(10),
  email: z.string().email().max(255).optional(),
})

const form = useZodForm({
  name: '',
  email: '',
}, schema);

function submit() {
  form.post('http://api.example.com')
}
</script>

<template>
  <form @submit.prevent="submit">
    <label for="name">Name</label>
    <br>
    <input name="name" v-model="form.name" />
    <p v-show="form.errors.name" style="color: red;">{{ form.errors.name }}</p>
    <br>
    <label for="email">Email</label>
    <br>
    <input name="email" v-model="form.email" />
    <p v-show="form.errors.email" style="color: red;">{{ form.errors.email }}</p>
    <br>
    <button type="submit">Submit</button>
  </form>
</template>
```

## Development

### Setup

```bash
$ pnpm install
```

### Build

```bash
$ pnpm --filter=@inertia-vue-form/zod build
```

### Debug

```bash
$ pnpm --filter=vue-ts run dev
```

## License
MIT
