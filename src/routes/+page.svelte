
  import WidgetStaticText from '$lib/components/Widgets/WidgetStaticText.svelte';
	import WidgetUserInput from '$lib/components/Widgets/WidgetUserInput.svelte';
	import WidgetTextGeneration from '$lib/components/Widgets/WidgetTextGeneration.svelte';
	import WidgetImageGeneration from '$lib/components/Widgets/WidgetImageGeneration.svelte';

  import { AppState } from '$lib/stores/appv2.svelte';
	import WidgetChatbot from '$lib/components/Widgets/WidgetChatbot.svelte';

  const appTitle = $AppState.appDetails.title;
  const appAuthor = $AppState.appDetails.author;
  const appUrl = $AppState.appDetails.url;


  const updateWidgetValue = (index: number, newValue: any) => {
    $AppState.widgets[index].value = newValue;
  }
</script>

<svelte:head>
  <title>{appTitle}</title>
</svelte:head>

<main class="party-body">
  <div class="party-header">
    <h1>
      {appTitle}
    </h1>
  </div>

  <div class="party-widget-list">
    {#each $AppState.widgets as widget, index}
      {#if widget.type == "static-text"}
        <WidgetStaticText title={ widget.title } />
      {:else if widget.type == "text-input"}
        <WidgetUserInput title={ widget.title } />
      {:else if widget.type == "inferred-text"}
        <WidgetTextGeneration title={ widget.title } />
      {:else if widget.type == "chat"}
        <WidgetChatbot title={ widget.title } />
      {:else if widget.type == "image"}
        <WidgetImageGeneration title={ widget.title } />
      {/if}
    {/each}
  </div>

 
</main>
