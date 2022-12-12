<script>
    export let company = 'Jensen Partners';
    export let fullname;
    export let pronouns;
    export let title;
    export let email;
    export let phone;
    export let avatar;
</script>

<style>
    img {
        height: revert;
        max-width: revert;
    }

    .banner {
        height: 150px;
    }

    td {
        text-align: left;
    }

    a {
        text-decoration: underline;
        color: #143954;
    }
</style>

<table border="0" cellpadding="0" cellspacing="0" style="width: auto; font-family: arial; font-size: 13px; line-height: 18px; color: #333333; text-decoration: none;" width="auto">
	<tbody>
		<tr>
	{#if avatar}
    <td style="vertical-align: top; padding: 25px 20px 0 10px;" valign="top" width="1"><a href="https://jensen-partners.com"><img src="{avatar}" width="50" alt="logo" class="mask mask-circle"/></a><br /><br />
    <a href="http://twitter.com/JensenPartners" target="_blank" rel="noreferrer"><img alt="twitter logo" src="images/twitter-circle-filled.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a> 
    <a href="http://linkedin.com/company/jensen-partners" target="_blank" rel="noreferrer"><img alt="linkedin logo" src="images/linkedin-with-circle.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a>
    <br /><br />
    </td>
    {:else}
    <td style="vertical-align: top; padding: 25px 20px 0 10px;" valign="top" width="1"><a href="https://jensen-partners.com"><img src="images/jp-logo.svg" width="50" alt="logo"/></a><br /><br />
    <a href="http://twitter.com/JensenPartners" target="_blank" rel="noreferrer"><img alt="twitter logo" src="images/twitter-circle-filled.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a> 
    <a href="http://linkedin.com/company/jensen-partners" target="_blank" rel="noreferrer"><img alt="linkedin logo" src="images/linkedin-with-circle.svg" style="width: 20px; vertical-align: bottom; padding-right: 1px; padding-top: 2px; padding-bottom: 2px; display: inline-block;" width="20" /></a>
    <br /><br />
    </td>
    {/if}
      <td style="vertical-align: top;" valign="top">
            <!-- Second Table start -->
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
						<a href="https://jensen-partners.com">jensen-partners.com</a><br />
                        <br />
                        <hr>
                        <br /></td>
					</tr>
				</tbody>
			</table>
            <!-- Second Table finish -->
			</td>
		</tr>
		<tr>
			<td colspan="2"><img src="images/signature-awards.png" alt="banner" class="banner" />
        </td>
		</tr>
	</tbody>
</table>