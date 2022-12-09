<script>
    import SignatureJP from "./SignatureJP.svelte";
    import SignatureDM from "./SignatureDM.svelte";
    import Tutorial from "./Tutorial.svelte";
    import { slide } from 'svelte/transition';
    
    let toastDelay = 10000; //10 Seconds

    let fullname = '';
    let title = '';
    let email = '';
    let phone = '';
    let pronouns = '';
    let signature;
    let signature2;
    let visible = false;
    let visible2 = false;
    let avatar;
    let fileinput;
	
	const onFileSelected =(e)=>{
        let image = e.target.files[0];
            let reader = new FileReader();
            reader.readAsDataURL(image);
            reader.onload = e => {
                 avatar = e.target.result
            };
    };

    function hideToast(toastDelay) {
        setTimeout(() => {visible = false}, toastDelay);
        setTimeout(() => {visible2 = false}, toastDelay);
    };

    function copySignatureJP() {
        var range = document.createRange();
        range.selectNode(document.getElementById("sigJP"));
        window.getSelection().removeAllRanges();
        window.getSelection().addRange(range);
        document.execCommand("copy");
        window.getSelection().removeAllRanges();
        visible = true;
        setTimeout(() => {visible = false}, toastDelay);
    };
    
    function copySignatureDM() {
        var range = document.createRange();
        range.selectNode(document.getElementById("sigDM"));
        window.getSelection().removeAllRanges();
        window.getSelection().addRange(range);
        document.execCommand("copy");
        window.getSelection().removeAllRanges();
        visible2 = true;
        setTimeout(() => {visible2 = false}, toastDelay);
    };

    function scrollIntoView() {
		const el = document.querySelector('#tutorial');
		if (!el) return;
        el.scrollIntoView({
            behavior: 'smooth'
        });
    };

</script>
<div class="max-w-full justify-center text-center p-8">


<h3 class="text-4xl font-bold py-3 mx-auto max-w-md">JP & DM <hr class="w-12 my-4 mx-auto border-info"> Email Signature Generator</h3>
<div class="mx-auto justify-center max-w-md py-4 pb-8">
    <span>Fill out the form below to populate the generated signatures with your own information</span>
</div>
<hr class="max-w-sm pt-4 pb-2 mx-auto border-info">
<form action="" class="mx-auto max-w-md justify-center pb-8">
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="fullname" class="label font-medium pb-1">
            <span class="label-text">Name*</span>
        </label>
        <input id="fullname" name="fullname" type="text" placeholder="First Last" bind:value={fullname} class="input input-bordered w-full max-w-md" />
    </div>
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="pronouns" class="label font-medium pb-1">
            <span class="label-text">Pronouns*</span>
        </label>
        <label class="input-group max-w-md">
            <select class="select select-bordered w-1/2 max-w-md" placeholder="Choose an option" bind:value={pronouns}>
                <option disabled selected value="">Choose an option</option>
                <option>He/Him/His</option>
                <option>She/Her/Hers</option>
                <option>They/Them/Theirs</option>
            </select>
          <input type="text" placeholder="or enter a custom value" class="input input-bordered w-1/2 max-w-md" bind:value={pronouns}/>
        </label>
      </div>
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="title" class="label font-medium pb-1">
            <span class="label-text">Title*</span>
        </label>
        <input id="title" name="title" type="text" placeholder="Job Title" bind:value={title} class="input input-bordered w-full max-w-md" />
    </div>
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="email" class="label font-medium pb-1">
            <span class="label-text">Email*</span>
        </label>
        <input id="email" name="email" type="email" placeholder="example@example.com" bind:value={email} class="input input-bordered w-full max-w-md" />
    </div>
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="phone" class="label font-medium pb-1">
            <span class="label-text">Mobile Phone*</span>
        </label>
        <input id="phone" name="phone" type="tel" placeholder="+1 999-999-9999" bind:value={phone} class="input input-bordered w-full max-w-md" />
    </div>
    <div class="form-control w-full max-w-md py-2 mx-auto justify-center">
        <label for="avatar" class="label font-medium pb-1">
            <span class="label-text">Custom Avatar (not required)</span>
        </label>
        <input id="avatar" name="avatar" type="file" class="file-input file-input-bordered w-full max-w-md" accept=".jpg, .jpeg, .png, .svg" on:change={(e)=>onFileSelected(e)} bind:value={fileinput} />
    </div>
</form>
<hr class="w-12 mt-2 mx-auto border-info">

<div class="max-w-2xl rounded-md mx-auto bg-primary-content h-auto mt-8 mb-8">
    <div class="w-full bg-base-200 py-3 rounded-t h-auto">
        <h3 class="text-lg font-bold mx-auto max-w-md">Generated Jensen Partners Signature</h3>
        <div class="w-full max-w-lg pt-3 mx-auto">
            <button class="btn btn-primary w-full max-w-lg" on:click={copySignatureJP}>Copy Signature to Clipboard</button>
            {#if visible}
            <div transition:slide class="toast bg-base-300 shadow rounded-md m-6 {visible ? 'visible' : ''}" id="toastJP">
                <div class="card-actions justify-end">
                    <button class="btn btn-circle btn-sm" on:click={hideToast}>
                      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" /></svg>
                    </button>
                </div>
                <div class="alert alert-success text-white justify-center max-w-xs mx-auto my-2">
                  <div>
                    <span>Successfully Copied to Clipboard
                  </div>
                </div>
                <p>You can now paste the generated signature directly into Outlook</p>
                    <a href="#tutorial" on:click|preventDefault={scrollIntoView} on:click={hideToast} class="text-info"><span>Click here for a tutorial</span></a>
            </div>
            {/if}
        </div>
    </div>
    <div class="w-full bg-primary-content h-auto rounded-b-md p-2">
            <div bind:this={signature} id="sigJP">
                {#key fileinput}
                <SignatureJP {fullname} {pronouns} {title} {email} {phone} {avatar}/>
                {/key}
            </div>
    </div>
</div>
<div class="max-w-2xl rounded-md mx-auto bg-primary-content h-auto mb-8">
    <div class="w-full bg-base-200 py-3 rounded-t h-auto">
        <h3 class="text-lg font-bold mx-auto max-w-md">Generated DiversityMetrics Signature</h3>
        <div class="w-full max-w-lg pt-3 mx-auto">
            <button class="btn btn-primary w-full max-w-lg" on:click={copySignatureDM}>Copy Signature to Clipboard</button>
            {#if visible2}
            <div transition:slide class="toast bg-base-300 shadow rounded-md m-6 {visible2 ? 'visible' : ''}" id="toastDM">
                <div class="card-actions justify-end">
                    <button class="btn btn-circle btn-sm" on:click={hideToast}>
                      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" /></svg>
                    </button>
                </div>
                <div class="alert alert-success text-white justify-center max-w-xs mx-auto my-2">
                  <div>
                    <span>Successfully Copied to Clipboard
                  </div>
                </div>
                <p>You can now paste the generated signature directly into Outlook</p>
                    <a href="#tutorial" on:click|preventDefault={scrollIntoView} on:click={hideToast} class="text-info"><span>Click here for a tutorial</span></a>
            </div>
            {/if}
        </div>
    </div>
    <div class="w-full bg-primary-content h-auto rounded-b-md p-2">
            <div bind:this={signature2} id="sigDM">
                {#key fileinput}
                <SignatureDM {fullname} {pronouns} {title} {email} {phone} {avatar} />
                {/key}
            </div>
    </div>
</div>
<div id="tutorial"></div>
<Tutorial />

</div>



