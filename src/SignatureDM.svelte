<script>
    import { onMount } from 'svelte';
    
    export let company = 'Jensen DiversityMetrics™';
    export let fullname;
    export let pronouns;
    export let title;
    export let email;
    export let phone;
    export let avatar;

    function copySigDM() {
    onMount(() => {
            let data = document.querySelector('#sigDM');
		    data.select();
		    document.execCommand('copy');
	});
    };
    
</script>

<style>
    img {
        height: revert;
        max-width: revert;
    }

    a {
        text-decoration: underline;
        color: #143954;
    }

    td {
        text-align: left;
    }
</style>

<table border="0" cellpadding="0" cellspacing="0" style="width: auto; font-family: arial; font-size: 13px; line-height: 18px; color: #333333; text-decoration: none;" width="auto">
	<tbody>
	<tr>
    {#if avatar}
	<td style="vertical-align: top; padding: 50px 20px 0 10px;" valign="top" width="1"><a href="https://jensendiversitymetrics.com"><img src="{avatar}" width="50" alt="logo" class="mask mask-circle"/></a>
    </td>
    {:else}
    <td style="vertical-align: top; padding: 50px 20px 0 10px;" valign="top" width="1"><a href="https://jensendiversitymetrics.com"><img src="images/jdm-logo-simple.png" width="50" alt="logo"/></a>
    </td>
    {/if}
      <td style="vertical-align: top;" valign="top">
			<table border="0" cellpadding="0" cellspacing="0" style="vertical-align: top;" valign="top" width="auto">
				<tbody>
					<tr style="vertical-align: top;" valign="top">
						<td><b style="font-style:italic; font-size: larger;">{fullname} ({pronouns})</b><br />
                        <span>{title} at {company}</span><br />
						<br />
						Email: {email}<br />
                        {#if phone}
						Phone: +1 212-457-0062 | Mobile: {phone}<br />
                        {:else}
                        Phone: +1 212-457-0062<br />
                        {/if}
						<br />
						New York | Miami | London | Hong Kong<br />
                        <a href="https://jensendiversitymetrics.com">jensendiversitymetrics.com</a><br />
						<br />
                        <hr>
                        <br />
                            <a href="https://twitter.com/diversitymetric" target="_blank" rel="noreferrer"><img alt="twitter logo" src="images/twitter-circle-filled.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a> 
                            <a href="https://www.linkedin.com/company/jensendiversitymetrics/" target="_blank" rel="noreferrer"><img alt="linkedin logo" src="images/linkedin-with-circle.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a>
                        <br />
                    </td>
					</tr>
				</tbody>
			</table>
			</td>
		</tr>
	</tbody>
</table>