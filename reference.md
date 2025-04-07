# Reference

## Generate

<details><summary><code>client.generate.<a href="/src/api/resources/generate/client/Client.ts">generateControllerCreateGeneration</a>({ ...params }) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generate.generateControllerCreateGeneration({
    model: "lipsync-2",
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

**requestOptions:** `Generate.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generate.<a href="/src/api/resources/generate/client/Client.ts">generateControllerGetGeneration</a>(id) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generate.generateControllerGetGeneration("id");
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

**id:** `string` — Job ID

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generate.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generate.<a href="/src/api/resources/generate/client/Client.ts">generateControllerCancelGeneration</a>(id) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generate.generateControllerCancelGeneration("id");
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

**id:** `string` — Job ID to cancel

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generate.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.generate.<a href="/src/api/resources/generate/client/Client.ts">generateControllerGetGenerations</a>({ ...params }) -> Sync.Generation[]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generate.generateControllerGetGenerations();
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

**request:** `Sync.GenerateControllerGetGenerationsRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Generate.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Analyze

<details><summary><code>client.analyze.<a href="/src/api/resources/analyze/client/Client.ts">analyzeControllerGetCostEstimate</a>({ ...params }) -> Sync.EstimatedGenerationCost[]</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.analyze.analyzeControllerGetCostEstimate({
    model: "lipsync-2",
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

**requestOptions:** `Analyze.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>
