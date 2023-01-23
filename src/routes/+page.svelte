<script lang="ts">
  import Tree from "../Tree.svelte";
  import type { TreeData } from "../Tree.svelte";

  const treeData: TreeData = [
    {
      id: "books",
      children: [{ id: "1", children: [{ id: "bbb" }] }, { id: "2" }],
    },
    {
      id: "movies",
      children: [{ id: "3" }, { id: "4", children: [{ id: "aaa" }] }],
    },
  ];
</script>

<Tree data={treeData}>
  <svelte:fragment slot="node" let:node>{node.id}</svelte:fragment>
</Tree>
