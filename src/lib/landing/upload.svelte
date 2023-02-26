<script>
    import { Button, Label, Select, Dropzone } from 'flowbite-svelte';

    let model = '', files;

    const onSubmit = (event) => {
        event.preventDefault();
        console.log(model, files);
    }
</script>

<div class="container mx-auto flex justify-center items-center w-screen h-screen p-6">
    <div class="text-white w-full">
        <h1 class="text-4xl font-bold text-center">TNNT Model Demo</h1>

        <form class="mt-6 w-full max-w-[600px] mx-auto" on:submit={onSubmit}>
            <Label for="model">Select a model</Label>
            <Select id="model" class="mt-2" bind:value={model}>
                <option value="model1">First Model</option>
                <option value="model2">Second Model</option>
                <option value="model3">Third Model</option>
            </Select>

            <Label for="dropzone" class="mt-4">Upload a document</Label>
            <Dropzone id="dropzone" class="mt-2" bind:files={files}>
                {#if files && files.length}
                    <p class="text-sm tet-gray-500">
                        {files.length} file(s) selected
                    </p>
                {:else}
                    <svg aria-hidden="true" class="mb-3 w-10 h-10 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"></path></svg>
                    <p class="mb-2 text-sm text-gray-500 dark:text-gray-400"><span class="font-semibold">Click to upload</span> or drag and drop</p>
                    <p class="text-xs text-gray-500 dark:text-gray-400">PDF</p>
                {/if}
            </Dropzone>

            <div class="flex justify-center">
                <Button gradient color="purpleToBlue" class="mt-4 w-full" type="submit">Upload</Button>
            </div>
        </form>
    </div>
</div>
