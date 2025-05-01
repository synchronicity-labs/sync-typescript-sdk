# Reference

## Generations

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">create</a>({ ...params }) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generations.create({
    input: [
        {
            type: "video",
            url: "https://synchlabs-public.s3.us-west-2.amazonaws.com/david_demo_shortvid-03a10044-7741-4cfc-816a-5bccd392d1ee.mp4",
        },
        {
            type: "audio",
            url: "https://synchlabs-public.s3.us-west-2.amazonaws.com/david_demo_shortaud-27623a4f-edab-4c6a-8383-871b18961a4a.wav",
        },
    ],
    model: "lipsync-2",
    options: {
        sync_mode: "loop",
    },
});
```

</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Sync.CreateGenerationDto`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generations.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">get</a>(id) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generations.get("6533643b-aceb-4c40-967e-d9ba9baac39e");
```

</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**id:** `Sync.GenerationId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generations.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">list</a>({ ...params }) -> Sync.Generation[]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generations.list();
```

</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Sync.ListGenerationsRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generations.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">estimateCost</a>({ ...params }) -> Sync.EstimatedGenerationCost[]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generations.estimateCost({
    input: [
        {
            type: "video",
            url: "https://synchlabs-public.s3.us-west-2.amazonaws.com/david_demo_shortvid-03a10044-7741-4cfc-816a-5bccd392d1ee.mp4",
        },
        {
            type: "audio",
            url: "https://synchlabs-public.s3.us-west-2.amazonaws.com/david_demo_shortaud-27623a4f-edab-4c6a-8383-871b18961a4a.wav",
        },
    ],
    model: "lipsync-2",
    options: {
        sync_mode: "loop",
    },
});
```

</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `Sync.CreateGenerationDto`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generations.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>
