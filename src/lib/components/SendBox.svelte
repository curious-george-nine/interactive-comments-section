<script>
  export let data;
</script>

<div class="bg-white rounded-xl px-3 py-3">
  <div class="contents lg:flex lg:justify-between lg:gap-4">
    <div>
      <img
        src=""
        alt="icon"
        class="w-8 h-8 lg:w-auto lg:h-auto hidden lg:block"
      />
    </div>
    <textarea
      placeholder="Add a comment..."
      class="resize-none w-full border border-gray-400 px-4 py-3 rounded-lg mb-4"
    />
    <div class="flex justify-between lg:contents">
      <img
        src="../lib/{data.currentUser.image.webp}"
        alt="icon"
        class="w-8 h-8 lg:hidden"
      />
      <div>
        <button
          class="uppercase bg-indigo-500 text-white px-6 py-3 rounded-lg font-bold text-sm inline-block"
          >send</button
        >
      </div>
    </div>
  </div>
</div>
