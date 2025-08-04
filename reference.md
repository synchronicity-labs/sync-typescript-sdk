# Reference

## Batch

<details><summary><code>client.batch.<a href="/src/api/resources/batch/client/Client.ts">create</a>(input, { ...params }) -> Sync.CreateBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

API for [Batch Processing](/api-reference/guides/batch-processing). Available only for `Scale` and `Enterprise` plans.

</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.batch.create(fs.createReadStream("/path/to/your/file"), {
    webhook_url: "https://your-webhook-url.com/batch-webhook",
    dry_run: false,
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

**input:** `File | fs.ReadStream | Blob`

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.CreateBatchRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Batch.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.batch.<a href="/src/api/resources/batch/client/Client.ts">get</a>(id) -> Sync.BatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve details about a specific batch, including its current status, processing metrics, and output file URL when available.

</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.batch.get("batch_abc123");
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

**id:** `Sync.BatchId` — The unique identifier of the batch

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Batch.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.batch.<a href="/src/api/resources/batch/client/Client.ts">list</a>({ ...params }) -> Sync.BatchResponse[]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all batches for your organization with optional filtering by status and creation date. Results are ordered by creation date (newest first).

</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.batch.list();
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

**request:** `Sync.ListBatchesRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Batch.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

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
            url: "https://assets.sync.so/docs/example-video.mp4",
        },
        {
            type: "audio",
            url: "https://assets.sync.so/docs/example-audio.wav",
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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">createWithFiles</a>(video, audio, { ...params }) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```typescript
await client.generations.createWithFiles(
    fs.createReadStream("/path/to/your/file"),
    fs.createReadStream("/path/to/your/file"),
    {
        model: "lipsync-2",
    },
);
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

**video:** `File | fs.ReadStream | Blob | undefined`

</dd>
</dl>

<dl>
<dd>

**audio:** `File | fs.ReadStream | Blob | undefined`

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.CreateGenerationRequest`

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
            url: "https://assets.sync.so/docs/example-video.mp4",
        },
        {
            type: "audio",
            url: "https://assets.sync.so/docs/example-audio.wav",
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
