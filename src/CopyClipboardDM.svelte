<script>
	import { onMount } from 'svelte';
	
	export const signature2 = async => {
        let content = document.querySelector('#sigDM');
	
	    onMount(() => {
		    content.select();
		    document.execCommand('copy');
	});
    }

	
</script>

