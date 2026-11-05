# Reference

## Account

<details><summary><code>client.account.<a href="/src/api/resources/account/client/Client.ts">get</a>() -> Sync.AccountOverview</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get the account, plan, limits and balance behind these credentials. Call it before submitting work to check plan limits and remaining credits or free allowance, and after a 402, 403 or 429 to decide how to recover: `billingModel` says whether to top up credits (`credits`), pay or update the payment method (`usage`), upgrade (`free`) or contact sync. (`enterprise`). Send people to `billingUrl` for anything that needs a payment.
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
await client.account.get();
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

**requestOptions:** `Account.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Assets

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">list</a>({ ...params }) -> Sync.PaginatedAssetsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all assets in your organization's media library.
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
await client.assets.list({
    limit: 10,
    sortBy: "dateDesc",
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

**request:** `Sync.ListAssetsRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">get</a>(id) -> Sync.Asset</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a specific asset by ID.
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
await client.assets.get("550e8400-e29b-41d4-a716-446655440000");
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

**id:** `Sync.AssetId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">createUpload</a>({ ...params }) -> Sync.AssetUploadResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Request a presigned URL to upload a local file. PUT the file bytes to the returned uploadUrl with the same Content-Type, then register the file as an asset via POST /v2/assets using the returned url. Single uploads are capped at 5GB.
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
await client.assets.createUpload({
    fileName: "my-video.mp4",
    contentType: "video/mp4",
    size: 10485760,
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

**request:** `Sync.CreateAssetUploadRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">create</a>({ ...params }) -> Sync.Asset</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Register a media URL as a reusable asset and get back its id. Use the id in generation inputs (input[].assetId) or as a voice clone sample. To upload a local file, first request a presigned URL via POST /v2/assets/upload, PUT the file there, then register the returned url here. Registration verifies the upload happened and enforces plan limits on the actual file size.

projectId is optional. When provided it must reference a project in your organization — a stale or foreign id is rejected with a 422 and errorCode project_not_found; omit the field if you don't need the asset attached to a project.
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
await client.assets.create({
    url: "https://assets.sync.so/org-123/my-video.mp4",
    type: "VIDEO",
    name: "my-video.mp4",
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

**request:** `Sync.CreateAssetRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">update</a>(id, { ...params }) -> Sync.Asset</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update an asset's name or visibility. With API-key auth the asset must be owned by the key owner; organization-shared assets can only be updated from an admin/owner session. An asset you can view but not edit returns a 403 with errorCode asset_forbidden; an unknown id returns a 404 with errorCode asset_not_found.
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
await client.assets.update("550e8400-e29b-41d4-a716-446655440000", {
    name: "Renamed asset",
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

**id:** `Sync.AssetId`

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.UpdateAssetRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.assets.<a href="/src/api/resources/assets/client/Client.ts">delete</a>(id) -> Sync.DeleteAssetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete an asset. With API-key auth the asset must be owned by the key owner; organization-shared assets can only be deleted from an admin/owner session. An asset you can view but not delete returns a 403 with errorCode asset_forbidden; an unknown id returns a 404 with errorCode asset_not_found.
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
await client.assets.delete("550e8400-e29b-41d4-a716-446655440000");
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

**id:** `Sync.AssetId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Assets.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Batch

<details><summary><code>client.batch.<a href="/src/api/resources/batch/client/Client.ts">create</a>(input, { ...params }) -> Sync.CreateBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a batch processing job from a JSONL file. Requires a paid plan; free accounts get 402 `plan_feature_unavailable`. Send the file in multipart field `input` (or the accepted `file` alias); it must be 5 MB or smaller. On Scale and above a batch holds 20-500 records by default and is queued, holding one concurrency slot. Below Scale every record runs as a generation right away, so a batch holds 1 record up to your plan's concurrency limit: more records than that returns 400, and more records than your currently free generation slots returns 429 `concurrency_limit_reached`. Credit-billed plans reserve credits for the whole batch at submit and get 402 `insufficient_credits` when the balance is short. Each line must contain `request_id`, endpoint exactly `/v2/generate`, and a generation `payload`. To send the records as a JSON array instead of a file, use "Create Batch from Rows", the `application/json` form of the same endpoint. Errors name a refused record by its 1-based line, counting non-empty lines: dialogue edit refusals return it as `lineNumber`, other record errors only in `message`.
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

<details><summary><code>client.batch.<a href="/src/api/resources/batch/client/Client.ts">createFromRows</a>({ ...params }) -> Sync.CreateBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The `application/json` form of `POST /v2/batch`, the same endpoint as "Create Batch": send the records in a `rows` array instead of a JSONL file. Each row is the same object as one JSONL line and is validated the same way: 20-500 rows by default on Scale and above, 1 row up to your free generation slots below Scale, 5 MB or smaller when serialized as JSONL, unique `request_id` values, and endpoint exactly `/v2/generate`. Errors name a refused row by its line, where line N is `rows[N-1]`: dialogue edit refusals return it as `lineNumber`, other record errors only in `message`. Requires a paid plan. In early access, enabled per organization, a row's payload can carry `dialogueEdit` to render a completed preview from POST /v2/dialogue-edits: send one video input, the video the preview was made from, and no audio input. All dialogue edit rows in a batch must come from the same source video. Each row is expanded at submit into the request POST /v2/generate builds for that preview and is charged the same. A dialogue edit row that cannot be rendered refuses the whole batch with the `/v2/generate` errorCode (for example dialogue_edit_not_found, 422) and `lineNumber`. See [Batch Processing](/api-reference/guides/batch-processing).
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
await client.batch.createFromRows({
    rows: [
        {
            request_id: "line-2",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "fa350e8a-0c6b-50c3-96de-7e4ce81ed0ce",
                },
            },
        },
        {
            request_id: "line-3",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "ddaea593-cf1f-5916-aaef-c60ab5f63090",
                },
            },
        },
        {
            request_id: "line-4",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "532a08cd-becc-5630-8109-58d22206db7e",
                },
            },
        },
        {
            request_id: "line-5",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "68f897e5-78e3-55d3-9ca3-d8ba0d16c5c4",
                },
            },
        },
        {
            request_id: "line-6",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "f4aa2ca8-006d-5301-baf7-4ce543188328",
                },
            },
        },
        {
            request_id: "line-7",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "636f1dd4-f4e1-508d-8cdd-6dac1dd002a3",
                },
            },
        },
        {
            request_id: "line-8",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "8f6640f5-6139-5271-ab33-f43fc91fc1ad",
                },
            },
        },
        {
            request_id: "line-9",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "6c101a02-cdd8-5ec0-9df9-1ffea33a11bd",
                },
            },
        },
        {
            request_id: "line-10",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "258f60c2-b635-5ab6-a565-ae81a709e221",
                },
            },
        },
        {
            request_id: "line-11",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "09dc425b-4d7e-5813-8c6c-81bd38993a7b",
                },
            },
        },
        {
            request_id: "line-12",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "b93c54d3-28d6-5fa3-abaf-5220c38e31a1",
                },
            },
        },
        {
            request_id: "line-13",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "e8a1dea0-b3f9-5266-badd-f8a2aae77ea3",
                },
            },
        },
        {
            request_id: "line-14",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "a09967c4-8171-582f-8dba-1ba07d55f918",
                },
            },
        },
        {
            request_id: "line-15",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "39df4e4f-b23d-54ca-99a8-f29ec567790b",
                },
            },
        },
        {
            request_id: "line-16",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "0370783a-12d5-5dfb-8736-49118428df47",
                },
            },
        },
        {
            request_id: "line-17",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "a65eecc2-ad79-5123-acf7-e81a57b2422f",
                },
            },
        },
        {
            request_id: "line-18",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "a0200ef6-d140-50bb-9784-3b9e265be374",
                },
            },
        },
        {
            request_id: "line-19",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "06cc754a-b625-58c2-ad2d-74ec08fb517a",
                },
            },
        },
        {
            request_id: "line-20",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "32889341-cc9e-59c6-b18a-32bbb525c26e",
                },
            },
        },
        {
            request_id: "line-21",
            endpoint: "/v2/generate",
            payload: {
                model: "sync-3",
                input: [
                    {
                        type: "video",
                        url: "https://assets.sync.so/docs/example-video.mp4",
                    },
                ],
                dialogueEdit: {
                    id: "f6568dbc-0390-5227-b107-64c3842adb3b",
                },
            },
        },
    ],
    dry_run: true,
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

**request:** `Sync.CreateBatchFromRowsRequest`

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

## DialogueEdits

<details><summary><code>client.dialogueEdits.<a href="/src/api/resources/dialogueEdits/client/Client.ts">create</a>({ ...params }) -> Sync.DialogueEditJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Applies word-level edits to a transcript from `POST /v2/transcriptions` and synthesizes preview audio for the same window: only the edited spans are re-spoken in a voice cloned from the source, everything else stays the original recording. Poll `GET /v2/dialogue-edits/{id}` until `status` is `COMPLETED`, `COMPLETED_PARTIAL` or `FAILED`; a completed or partially completed job carries `previewAudioUrl`, the retimed `resultTranscript` and the edited regions as `resultSlots`. Edits that cannot be applied to the transcript are refused with a 400 before a job exists. An API-key request is admitted only for the whole video (leave startMs and endMs unset) and only when the organization's rollout enables segment lipsync and section expansion: a partial window is refused with errorCode `dialogue_edit_unsupported` (422), a rollout without both flags with `dialogue_edit_retime_required` (422), and a rollout that cannot be evaluated with `generation_infra_service_unavailable` (503; retry with backoff). Studio sessions may select a window. Normal billing, planning, duration and rate limits still apply.
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
await client.dialogueEdits.create({
    sourceVideoUrl: "https://assets.sync.so/docs/example-video.mp4",
    transcript: {
        segments: [
            {
                id: "seg_1",
                words: [
                    {
                        id: "w_1",
                        text: "The",
                        startMs: 120,
                        endMs: 260,
                    },
                    {
                        id: "w_2",
                        text: "quarterly",
                        startMs: 260,
                        endMs: 820,
                    },
                    {
                        id: "w_3",
                        text: "results",
                        startMs: 820,
                        endMs: 1240,
                    },
                ],
            },
        ],
        speakerCount: 1,
    },
    edits: [
        {
            kind: "change",
            wordId: "w_2",
            replacement: "annual",
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

**request:** `Sync.CreateDialogueEditDto`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DialogueEdits.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.dialogueEdits.<a href="/src/api/resources/dialogueEdits/client/Client.ts">get</a>(id) -> Sync.DialogueEditJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the job status and, once it completed, the preview audio url, the retimed transcript and the edited regions. `COMPLETED`, `COMPLETED_PARTIAL` and `FAILED` are terminal; `error.code` says why a job failed.
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
await client.dialogueEdits.get("7644754c-bdfc-4d51-a78f-e0cb0cbbd40f");
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

**id:** `Sync.DialogueEditJobId` — Dialogue edit job id.

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `DialogueEdits.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Errors

<details><summary><code>client.errors.<a href="/src/api/resources/errors/client/Client.ts">list</a>() -> Sync.ErrorCatalogEntry[]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full catalog of machine-readable error codes — each with a human-readable message and a suggested fix. It covers generation failures plus the coded errors returned by the assets, voices, and TTS endpoints (e.g. project_not_found, voice_not_found, asset_forbidden). This endpoint is unauthenticated. Pair it with the errorCode field returned on a failed generation or on a coded 4xx/5xx response so an agent can look up what went wrong and how to correct it without hard-coding error strings.
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
await client.errors.list();
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

**requestOptions:** `Errors.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Feedback

<details><summary><code>client.feedback.<a href="/src/api/resources/feedback/client/Client.ts">submit</a>({ ...params }) -> Sync.FeedbackReceipt</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Report a problem you hit with the API or the sync. MCP server, such as an error that didn't say what to fix, a wrong result, a missing capability, or a workaround you needed. Send one report per problem. The sync. team reviews reports daily. Works with an API key, an OAuth access token, or a Studio session. Submitting feedback doesn't change, retry, or cancel any job. Limited to 30 reports per minute per caller. Unknown body fields return 400.
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
await client.feedback.submit({
    kind: "confusing_error",
    severity: "major",
    message:
        "POST /v2/generate returned generation_input_video_inaccessible for a presigned URL that plays in a browser. Saying whether the URL had expired or was blocked would have helped.",
    tool: "generations.create",
    errorCode: "generation_input_video_inaccessible",
    generationId: "6533643b-acbb-4c4f-a5b3-5ba2e5ab6b5f",
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

**request:** `Sync.SubmitFeedbackRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Feedback.RequestOptions`

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

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a lip sync generation with `application/json` — provide each input by `url` or by `assetId` from an uploaded asset. For reusable or large local files, upload them first with POST /v2/assets/upload and pass the returned `assetId`; see [Asset Uploads](/developer-guides/asset-uploads). Use the multipart "Create Generation with Files" form only when uploading direct audio, video, or image file fields; it has a 5 GiB per-file application parser limit, subject to your plan and any lower proxy limits. Nested fields such as input, options, segments, outputAudio, dubParams, and dialogueEdit must be JSON strings in multipart requests. If a `text` input requires speech synthesis and the ElevenLabs provider is temporarily unavailable, the request returns errorCode elevenlabs_service_unavailable: 504 for provider timeouts and 503 for other provider outages for unkeyed requests. Keyed uncertain outcomes return 503 IDEMPOTENCY_OUTCOME_UNKNOWN instead. An API-key request that passes dialogueEdit is refused with errorCode dialogue_edit_retime_required (422) when the organization's rollout lacks segment lipsync and section expansion. A dialogueEdit that removes more speech than the surrounding footage can absorb returns errorCode dialogue_edit_removal_too_large (422). When the failing section can be identified, `dialogueEditSection` on the error names it; change it and create a new preview before submitting again. Retrying the same preview fails again. Send the optional Idempotency-Key header on the first request and reuse it with the same payload on retries. An accepted replay returns 200 with the original generation's current state and Idempotency-Replayed: true. A retry after that generation ended FAILED or REJECTED starts a new generation instead (201). An API-key request without the header that is identical to one your organization sent in the last 60 seconds returns 409 DUPLICATE_SUBMISSION with the original generationId; send a unique Idempotency-Key with each generation you intend. See [Idempotent Requests](/api-reference/guides/idempotency) for key validation, conflicts, retention, duplicates, and uncertain-outcome recovery.
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
    model: "sync-3",
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

**request:** `Sync.CreateGenerationJsonRequest`

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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">createWithFiles</a>(video, image, audio, { ...params }) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

The multipart/form-data form of `POST /v2/generate` — the same endpoint as "Create Generation", for uploading local files directly instead of passing URLs. Send each file under a field named for its type (`video`, `image`, `audio`), at most one of each. The application parser allows up to 5 GiB (5 × 1024³ bytes) per file, 3 files, 32 fields, 35 total parts, and 1 MiB per field. A file over the parser limit returns 413 generation_input_validation_failed, and a file over your plan limit returns 422 file_size_exceeds_plan_limit. Proxy limits may be lower; this ceiling does not guarantee a 5 GiB direct transfer. Each file is saved as an asset in your organization and passed to the generation by `assetId`. For large files, upload via POST /v2/assets/upload first and pass the `assetId`, so retries don't resend the file. Nested fields such as `input`, `options`, `segments`, `outputAudio`, `dubParams`, and `dialogueEdit` must be sent as JSON strings in multipart requests. Image inputs are sync-3 only. If a `text` input requires speech synthesis and the ElevenLabs provider is temporarily unavailable, the request returns errorCode elevenlabs_service_unavailable: 504 for provider timeouts and 503 for other provider outages for unkeyed requests. Keyed uncertain outcomes return 503 IDEMPOTENCY_OUTCOME_UNKNOWN instead. An API-key request that passes dialogueEdit is refused with errorCode dialogue_edit_retime_required (422) when the organization's rollout lacks segment lipsync and section expansion. A dialogueEdit that removes more speech than the surrounding footage can absorb returns errorCode dialogue_edit_removal_too_large (422). When the failing section can be identified, `dialogueEditSection` on the error names it; change it and create a new preview before submitting again. Retrying the same preview fails again. Send the optional Idempotency-Key header on the first request and reuse it with the same payload on retries. An accepted replay returns 200 with the original generation's current state and Idempotency-Replayed: true. A retry after that generation ended FAILED or REJECTED starts a new generation instead (201). An API-key request without the header that is identical to one your organization sent in the last 60 seconds returns 409 DUPLICATE_SUBMISSION with the original generationId; send a unique Idempotency-Key with each generation you intend. See [Idempotent Requests](/api-reference/guides/idempotency) for key validation, conflicts, retention, duplicates, and uncertain-outcome recovery.
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
await client.generations.createWithFiles(
    fs.createReadStream("/path/to/your/file"),
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

**image:** `File | fs.ReadStream | Blob | undefined`

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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">get</a>(id, { ...params }) -> Sync.Generation</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the current generation state. This /v2/generate/{id} route supports the wait, timeout and include options below.
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

**request:** `Sync.GetGenerationRequest`

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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">download</a>(id, { ...params }) -> string</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Obtain the available full output of a completed generation in your
organization. Authenticate with `x-api-key`; no Studio project or user
session is required. Any valid API key belonging to the generation's
organization can request the URL.

The successful response is an **unquoted URL in a text/plain body**,
not JSON, a redirect, or the video itself. Fetch that URL separately
without forwarding your API key.

```bash
download_url=$(curl --fail-with-body --silent --show-error \
  -H "x-api-key: $SYNC_API_KEY" \
  "https://api.sync.so/v2/generations/$GENERATION_ID/download") &&
curl --fail --location "$download_url" --output output.mov
```

The URL resolves an existing output using your organization's current
plan and billing-version eligibility. Free and watermark-required plans
receive the watermarked derivative when present. Entitled plans (such
as v2 Creator and v3 Starter or higher) receive the clean output when
available. Historical outputs can have the watermark burned in, so an
upgrade does not guarantee every old output becomes watermark-free.
Outputs created without a watermark can remain clean after a downgrade.
If no watermarked derivative exists, the resolver retains its existing
fallback to the original output; changing plans does not rewrite files.
This endpoint does not generate a new render or remove burned-in watermarks.

Signed S3 URLs request seven-day validity, but credential expiry,
revocation, access changes, or file deletion can make them unusable
sooner. Request this endpoint again for a fresh signed URL while the
output is still available. The selected S3 file is checked before
signing; a successful response does not guarantee future availability.
Older URL-only records return their stored URL unchanged, without
checking its availability or extending its original expiration.
These URLs are download credentials: keep them private.

Errors use the standard JSON error body and stable `errorCode`:

| Status | Code                              | Meaning / next step                                                            |
| ------ | --------------------------------- | ------------------------------------------------------------------------------ |
| 400    | —                                 | Invalid generation UUID.                                                       |
| 401    | —                                 | API key missing, invalid, or revoked.                                          |
| 404    | `generation_not_found`            | Missing, deleted, or outside your organization.                                |
| 404    | `generation_output_unavailable`   | No eligible output reference or the selected file is missing; contact support. |
| 409    | `generation_not_ready`            | Pending or processing; poll Get Generation until COMPLETED.                    |
| 422    | `generation_not_downloadable`     | Failed or rejected; inspect the generation error.                              |
| 503    | `generation_download_unavailable` | Storage lookup or signing failed; retry with backoff.                          |

Authentication also returns 422 for draft organizations. Requesting a
download URL does not create a project, incur a generation charge, or
restore deleted files.
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
await client.generations.download("id");
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

**request:** `Sync.GetGenerationDownloadRequest`

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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">estimateCost</a>({ ...params }) -> Sync.EstimatedGenerationCost</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Estimate a generation from its model and billable duration in seconds. Supply a finite positive duration and, optionally, a finite positive fps (defaults to 25 for credit-billed organizations and 30 otherwise). Set `workflow` to `translate-and-dub` to include dubbing; the response then carries a `breakdown`. `durationCheck` says whether your account and the model allow the quoted duration. No media is fetched and no generation is created. POST /v2/generate/estimate-cost is an alias of this endpoint. Invalid request fields return 400. If the billing calculation rejects the duration or frame rate, it returns 422 cost_estimate_unavailable without price fields.
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
await client.generations.estimateCost({
    model: "model",
    duration: 1.1,
    fps: undefined,
    workflow: undefined,
    reasoningEnabled: undefined,
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

**request:** `Sync.EstimateCostRequest`

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

<details><summary><code>client.generations.<a href="/src/api/resources/generations/client/Client.ts">delete</a>(id) -> Sync.ProjectGeneration</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a generation. Generations are organization-scoped, so any member — or an API key for the organization — can delete one. Only generations in a terminal state can be deleted; deleting one that is still processing returns 409 (errorCode `generation_not_deletable_while_processing`). Returns the deleted generation in its stored shape (`modelName`, `inputs`, `outputMediaUrl`, `deletedAt`), not the Get Generation shape.
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
await client.generations.delete("6533643b-aceb-4c40-967e-d9ba9baac39e");
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

## Models

<details><summary><code>client.models.<a href="/src/api/resources/models/client/Client.ts">list</a>() -> Sync.ModelInfo[]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List all available models for the authenticated user. Returns active (non-deprecated) models the user has access to, including any feature-flagged models enabled for their account.
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
await client.models.list();
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

**requestOptions:** `Models.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Organizations

<details><summary><code>client.organizations.<a href="/src/api/resources/organizations/client/Client.ts">getWebhookSecret</a>({ ...params }) -> Sync.WebhookSecretResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve your organization's webhook signing secret. This is a public, authenticated endpoint you can use to verify the `Sync-Signature` header on generation and batch webhook deliveries: Sync signs the raw JSON request body as HMAC-SHA256 over `${timestamp}.${rawBody}` and sends it as `Sync-Signature: t=<unix>,v1=<hmac_sha256>`. Store the full `whsec_...` value securely. `masked=true` returns a display-only value; do not use it as a verification secret. The same secret is available on the [webhooks settings page](https://sync.so/settings/webhooks).
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
await client.organizations.getWebhookSecret();
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

**request:** `Sync.GetWebhookSecretRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Organizations.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Projects

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">create</a>({ ...params }) -> Sync.Project</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a project to group related generations and assets. Pass the returned id as projectId on POST /v2/generate or POST /v2/assets to file them under this project so they show up together in Studio. Only name is required — visibility defaults to USER and mode to CREATOR. Supply a client-generated UUID as id for idempotent creation. A retry with the same id returns the existing project and ignores other request fields; an id owned by another user/organization or a deleted project returns 409.
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
await client.projects.create({
    id: "612bb64a-e7f4-40c1-977b-3e9797845637",
    name: "My API Project",
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

**request:** `Sync.CreateProjectRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">list</a>({ ...params }) -> Sync.PaginatedProjectsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List the projects in your organization, most recently updated first.
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
await client.projects.list({
    limit: 10,
    sortBy: "updatedAt",
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

**request:** `Sync.ListProjectsRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">get</a>(id) -> Sync.Project</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a project by id.
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
await client.projects.get("612bb64a-e7f4-40c1-977b-3e9797845637");
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

**id:** `Sync.ProjectId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">attachAsset</a>(id, { ...params }) -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Attach an existing asset to a project so it is grouped under the project alongside its generations. The asset must belong to your organization and not be deleted. This is idempotent — re-attaching an asset that is already linked succeeds without creating a duplicate. Returns 204 No Content on success.
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
await client.projects.attachAsset("612bb64a-e7f4-40c1-977b-3e9797845637", {
    assetId: "8f14e45f-ceea-467d-9a1b-3e4d5c6f7a8b",
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

**id:** `Sync.ProjectId`

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.AttachProjectAssetRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">detachAsset</a>(id, assetId) -> void</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Detach an asset from the project's draft content, such as its thumbnail. The asset remains in the project's asset library and keeps its access grants. Attaching it again restores the link. This operation is idempotent, including when the link is already detached or absent. Returns 204 No Content. An inaccessible project returns 404. An API key without an owner returns 422.
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
await client.projects.detachAsset("id", "assetId");
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

**id:** `Sync.ProjectId`

</dd>
</dl>

<dl>
<dd>

**assetId:** `Sync.AssetId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">update</a>(id, { ...params }) -> Sync.Project</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update a project's name, description, visibility, or mode. Only the fields you provide are changed.
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
await client.projects.update("612bb64a-e7f4-40c1-977b-3e9797845637", {
    name: "Renamed Project",
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

**id:** `Sync.ProjectId`

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.UpdateProjectRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.projects.<a href="/src/api/resources/projects/client/Client.ts">delete</a>(id) -> Sync.DeleteProjectResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a project. A project can't be deleted while any of its generations are queued or processing — wait for those to finish, then retry. Deletion soft-deletes the project and its generations, removes its asset links, and soft-deletes assets with no other active project. Assets linked to another active project are retained.
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
await client.projects.delete("612bb64a-e7f4-40c1-977b-3e9797845637");
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

**id:** `Sync.ProjectId`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Projects.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Transcriptions

<details><summary><code>client.transcriptions.<a href="/src/api/resources/transcriptions/client/Client.ts">create</a>({ ...params }) -> Sync.TranscriptionJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Starts a word-level transcription of a window of a video, the first step of a dialogue edit. Provide exactly one of `sourceVideoUrl` or `sourceAudioUrl`, both hosted in sync. storage (upload via `POST /v2/assets/upload`). Passing pre-extracted audio skips the server-side download and transcode. Poll `GET /v2/transcriptions/{id}` until `status` is `COMPLETED`, then pass the `transcript` and your edits to `POST /v2/dialogue-edits`. An identical source and window returns the existing job instead of starting a new one. Transcription is not billed.
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
await client.transcriptions.create({
    sourceVideoUrl: "https://assets.sync.so/docs/example-video.mp4",
    endMs: 30000,
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

**request:** `Sync.CreateTranscriptionDto`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Transcriptions.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.transcriptions.<a href="/src/api/resources/transcriptions/client/Client.ts">get</a>(id) -> Sync.TranscriptionJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the job status and, once `status` is `COMPLETED`, the word-level transcript. `COMPLETED` and `FAILED` are terminal; `error.code` says why a job failed.
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
await client.transcriptions.get("6533643b-aceb-4c40-967e-d9ba9baac39e");
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

**id:** `Sync.TranscriptionJobId` — Transcription job id.

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Transcriptions.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Tts

<details><summary><code>client.tts.<a href="/src/api/resources/tts/client/Client.ts">create</a>({ ...params }) -> Sync.TtsGenerationResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Synthesize speech from a script and get back a hosted audio URL. The returned url can be reused as an audio input in POST /v2/generate to lip sync the synthesized take. voiceId accepts an ElevenLabs voice id (discover via GET /v2/voices) or the id of a voice cloned via POST /v2/voices. Free-tier keys share the monthly ElevenLabs allowance; paid plans are billed per use.

A voiceId that does not resolve returns a 422 with errorCode voice_not_found. If a voice from your own ElevenLabs account stops resolving, the connected API key may be invalid — provider failures surface errorCode elevenlabs_api_key_invalid (reconnect it in Settings > Integrations) or elevenlabs_quota_exceeded (402) when your own ElevenLabs quota is exhausted. Temporary ElevenLabs provider failures return errorCode elevenlabs_service_unavailable: 504 for provider timeouts and 503 for other provider outages. Retry those requests with backoff and include the requestId if you contact support. A voice with an unresolved ElevenLabs restriction returns errorCode voice_verification_required or voice_blocked (both normally 422, or 400 when the pre-synthesis check was unavailable), or voice_access_denied (400). The required action depends on the code and on whether the voice is from your own connected ElevenLabs account — see the Error Handling guide.
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
await client.tts.create({
    script: "Hey \u2014 thanks for trying sync. labs.",
    voiceId: "EXAVITQu4vr4xnSDxMaL",
    provider: "elevenlabs",
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

**request:** `Sync.CreateTtsRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Tts.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.tts.<a href="/src/api/resources/tts/client/Client.ts">createJob</a>({ ...params }) -> Sync.TtsJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a job for asynchronous speech synthesis. Returns 202 with the accepted job and a `Location` header pointing at GET /v2/tts/jobs/{id}; poll that endpoint for the result. Accepts the same body as POST /v2/tts. API-key requests require your organization to be enabled for the asynchronous TTS rollout; otherwise the request returns 503.
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
await client.tts.createJob({
    script: "Hey \u2014 thanks for trying sync. labs.",
    voiceId: "EXAVITQu4vr4xnSDxMaL",
    provider: "elevenlabs",
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

**request:** `Sync.SubmitTtsJobRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Tts.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.tts.<a href="/src/api/resources/tts/client/Client.ts">getJob</a>(id) -> Sync.TtsJob</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a text-to-speech job by id. While the job is PENDING or PROCESSING, the response carries a `Retry-After: 3` header. The header is absent once the job reaches a terminal state (SUCCESS or FAILED).
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
await client.tts.getJob("6533643b-aceb-4c40-967e-d9ba9baac39e");
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

**id:** `string` — The job id returned when the job was submitted.

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Tts.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

## Voices

<details><summary><code>client.voices.<a href="/src/api/resources/voices/client/Client.ts">list</a>({ ...params }) -> Sync.Voice[]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

List the voices available to your organization — built-in ElevenLabs voices plus any you have cloned. Use a voice's id as voiceId in POST /v2/tts and in generation text inputs. A voice that carries a `restriction` cannot currently synthesize speech — check `restriction` and choose another voice. Voice availability can change over time, so re-check it rather than assuming a voice stays usable.
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
await client.voices.list();
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

**request:** `Sync.ListVoicesRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Voices.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.voices.<a href="/src/api/resources/voices/client/Client.ts">get</a>(id, { ...params }) -> Sync.Voice</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve a single voice by the same id values GET /v2/voices exposes — a built-in ElevenLabs voice id or the UUID of a voice cloned by your organization. A missing or foreign-organization id returns a 404 with errorCode voice_not_found.
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
await client.voices.get("EXAVITQu4vr4xnSDxMaL");
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

**id:** `string` — The voice id — a built-in provider voice id or a cloned voice UUID.

</dd>
</dl>

<dl>
<dd>

**request:** `Sync.GetVoiceRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Voices.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.voices.<a href="/src/api/resources/voices/client/Client.ts">clone</a>({ ...params }) -> Sync.ClonedVoiceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Clone a custom voice from an audio or video sample and get back its id for use in POST /v2/tts and generation text inputs.

The exact sequence for a local file: (1) request a presigned URL via POST /v2/assets/upload, (2) PUT the file bytes to the returned uploadUrl, (3) clone from the returned url (or register it via POST /v2/assets and clone from the assetId). Samples must be hosted in sync. labs storage — external URLs are rejected with errorCode voice_sample_upload_required. Video sources have their audio track extracted automatically (first 2 minutes). Video sources staged for extraction are limited to 1 GiB (1,073,741,824 bytes); larger sources return 413 voice_sample_source_too_large. This endpoint allows 10 requests per hour per API key (or per signed-in user).

For best results use 30 seconds to 2 minutes of clear, single-speaker speech without background music or noise. Samples that are too short are rejected with errorCode voice_sample_too_short. Clone slots are limited per plan (403 voice_clone_limit_reached) and voice names must be unique within your organization (409 voice_name_conflict). Sample source problems return 422 (voice_sample_not_accessible, voice_sample_type_unsupported, voice_sample_upload_required, voice_sample_extraction_failed); invalid or too-short samples return 400 (voice_sample_invalid, voice_sample_too_short). A 429 may mean the request-rate limit was exceeded or shared provider capacity is busy (voice_clone_busy); follow the response retry guidance. Provider outages return 503 (elevenlabs_service_unavailable).
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
await client.voices.clone({
    name: "My Narrator",
    provider: "elevenlabs",
    assetId: "550e8400-e29b-41d4-a716-446655440000",
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

**request:** `Sync.CreateVoiceRequest`

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Voices.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>

<details><summary><code>client.voices.<a href="/src/api/resources/voices/client/Client.ts">delete</a>(id) -> boolean</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Delete a cloned voice, freeing a clone slot. Unknown ids return 404 with errorCode `voice_not_found`.
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
await client.voices.delete("7f9c2b3a-1d4e-4a8b-9c0d-2e3f4a5b6c7d");
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

**id:** `string` — The Sync UUID returned as id when the voice was cloned.

</dd>
</dl>

<dl>
<dd>

**requestOptions:** `Voices.RequestOptions`

</dd>
</dl>
</dd>
</dl>

</dd>
</dl>
</details>
