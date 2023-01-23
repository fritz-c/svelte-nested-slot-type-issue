<script context="module" lang="ts">
  export type TreeNode = { id: string; children?: TreeData };
  export type TreeData = TreeNode[];
</script>

<script lang="ts">
  export let data: TreeData;
</script>

<ul>
  {#each data as node (node.id)}
    <li>
      <slot name="node" {node} />
      {#if node.children}
        <svelte:self data={node.children}>
          <!--
            Issue: both let:node and {node} in the element below lack types, and
            fall back to `any`
          -->
          <slot name="node" slot="node" let:node {node} />
        </svelte:self>
      {/if}
    </li>
  {/each}
</ul>
