<script lang="ts">
import { Link } from '@podman-desktop/ui-svelte';

import type { ProviderInfo } from '/@api/provider-info';

export let provider: ProviderInfo;
</script>

{#if provider.links.length > 0}
  <div class="mt-2 flex relative w-full content-stretch items-center flex-row justify-around grow flex-nowrap">
    {#each provider.links as link, index (index)}
      {#if link.group === undefined}
        <Link class="text-base" on:click={(): Promise<void> => window.openExternal(link.url)}>
          {link.title}
        </Link>
      {/if}
    {/each}
  </div>
{/if}
