<script>
  import Comment from "$lib/components/Comment.svelte";
  import DeleteModal from "$lib/components/DeleteModal.svelte";
  import SendBox from "$lib/components/SendBox.svelte";
  import { onMount } from "svelte";

  let toggleDeleteModalOpen = false;

  async function fetchComments() {
    const res = await fetch(`/api/`);
    const data = await res.json();

    console.log(data);

    return data;
  }

  onMount(() => {
    fetchComments();
  });

  function showModal() {
    toggleDeleteModalOpen = true;
  }

  function hideModal() {
    toggleDeleteModalOpen = false;
  }
</script>

<section class="py-7 px-3 lg:w-1/2 lg:mx-auto">
  {#await fetchComments()}
    loading
  {:then data}
    <div class="space-y-3">
      {#each data.comments as comment}
        <Comment score={comment.score}>
          <div slot="pfp" class="contents">
            <img src="/{comment.user.image.png}" alt="" class="w-8" />
          </div>
          <div slot="username" class="contents">
            {comment.user.username}
            {#if comment.user.username == data.currentUser.username}
              you
            {/if}
          </div>
          <div slot="createdAt" class="contents text-gray-500">
            {comment.createdAt}
          </div>
          <div slot="contents" class="contents text-gray-600">
            {comment.content}
          </div>
        </Comment>
        {#each comment.replies as reply, index}
          <Comment
            isReply={true}
            score={reply.score}
            isMine={reply.user.username == data.currentUser.username}
            isLast={comment.replies.length - 1 == index}
            on:deleteClick={showModal}
          >
            <div slot="pfp" class="contents">
              <img src="/{reply.user.image.webp}" alt="" class="w-8" />
            </div>
            <div slot="username" class="contents">
              {reply.user.username}
            </div>
            <div slot="createdAt" class="contents text-gray-500">
              {reply.createdAt}
            </div>
            <div slot="contents" class="contents text-gray-600">
              <span class="text-blue-800 font-bold">@{reply.replyingTo}</span>
              {reply.content}
            </div>
          </Comment>
        {/each}
      {/each}
      <SendBox {data} />
    </div>
  {/await}
</section>

{#if toggleDeleteModalOpen}
  <DeleteModal on:hideModal={() => hideModal()} />
{/if}
