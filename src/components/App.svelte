<script>
  import { Alert } from "flowbite-svelte";
  import { APP_STATUS, appStatus } from "../store.ts";
  import StepUploading from "./StepUploading.svelte";
  import StepLoading from "./StepLoading.svelte";
  import StepChat from "./StepChat.svelte";
</script>

{#if $appStatus === APP_STATUS.INIT}
  <StepUploading />
{:else if $appStatus === APP_STATUS.LOADING}
  <StepLoading />
{:else if $appStatus === APP_STATUS.ERROR}
  <Alert>
    <span class="font-medium">¡Ups, algo malo ha pasado!</span>
    Hay un error al cargar la página. Por favor, intenta recargar la página.
  </Alert>
{:else if $appStatus === APP_STATUS.CHAT_MODE}
  <StepChat />
{:else}
  <Alert>
    <span class="font-medium">Acción no reconocida</span>
    Este estado de la aplicación no está reconocido.
  </Alert>
{/if}
