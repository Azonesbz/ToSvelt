<script>
  import Taskcontainer from "./lib/Taskcontainer.svelte";
</script>

<head>
  <link rel="stylesheet" href="/app.css">
</head>

<main class="min-h-screen h-screen flex items-center justify-center">
  <nav class="fixed min-w-screen w-full h-[75px] flex items-center justify-center inset-0">
    <h1>todoapp</h1>
  </nav>
  <section class="h-[80vh] w-full flex items-center justify-center px-[200px]">
    <Taskcontainer/>
  </section>
</main>
