<script>
  import Card from "./Card.svelte";
  export let post
  let evento = 'aqui no hay nada'
  function verMas(e){
    alert('Ver mas información')
    console.log(e)
    evento = e.detail.id
  }

  function favorito(event){
    alert('ahora es favorito')
    console.log(event)
    evento = event.detail
  }
</script>

<div class="row mt-3">
  {#each post as item}
    <div class="col-sm-4">
      <Card
        titulo={item.titulo}
        descripcion={item.descripcion}
        imagen={item.imagen}
        on:ver-mas={verMas}
        on:favorito={favorito} />
    </div>
  {/each}
</div>
<h1>{evento}</h1>
