<script>
	import Header from './Design/Header.svelte'
	import InputCustom from './Design/InputCustom.svelte'
	import CardGrid from './Posts/CardGrid.svelte'
	import Jumbotron from './Design/Jumbotron.svelte'
	

	const color = "warning"

	let titulo = ''
	let descripcion = ''
	let imagen = ''
	
	let show = false

	let post = [
		{
			id:'1',
			titulo:'Trabajando con svelte',
			descripcion:'Realizando el curso de svelte temprano por la mañana',
			imagen:'https://cdn.pixabay.com/photo/2019/09/03/04/35/macaw-4448598_960_720.jpg'
		},
		{
			id:'2',
			titulo:'Trabajando con vue',
			descripcion:'Realizando el curso de svelte temprano por la tarde',
			imagen:'https://cdn.pixabay.com/photo/2017/07/08/17/44/daisies-2485064_960_720.jpg'
		},
		{
			id:'3',
			titulo:'Trabajando con Angular',
			descripcion:'Realizando el curso de svelte temprano por la noche',
			imagen:'https://cdn.pixabay.com/photo/2019/10/18/17/35/flowers-4559785_960_720.jpg'
		}

	]

	function agregarPost(){
		const nuevoPost = {
			id: Math.random().toString(),
			titulo:titulo,
			descripcion:descripcion,
			imagen:imagen
		}

		post = [nuevoPost, ...post]
	}
</script>

<Header titulo="Componentes" {color}  />

<div class="container" >

Mostrar jumbotron <input type="checkbox" bind:checked={show}>

{#if show}
	<Jumbotron nombre="Mis Componentes" let:mostrar={mostrar}>
	<span slot="subtitulo">
		Curso de svelte
	</span>
	<span slot="parrafo">
		Contenido del curso en un parrafo
	</span>
	<div class:mostrar>
		{#if mostrar}
			<hr>
			<button class="btn btn-danger" >Boton</button>
		{:else}
			<h2>Coloca el mouse encima</h2>
		{/if}
	</div>
</Jumbotron>
{/if}

<CardGrid {post} />

<form on:submit|preventDefault={agregarPost}>
	<!-- <input type="text" placeholder="Titulo" bind:value={titulo} >
	<input type="text" placeholder="Descripcion" bind:value={descripcion} >
	<input type="text" placeholder="imagen" bind:value={imagen} >
	<button type="submit" class="btn btn-info" >Guardar</button> -->

	<InputCustom 
		type="text"
		nombre="Titulo"
		id="titulo"
		placeholder="Titulo"
		value={titulo}
		on:input={event => (titulo = event.target.value) }
	/>

	<InputCustom 
		type="text"
		nombre="Imagen"
		id="imagen"
		placeholder="Imagen"
		value={imagen}
		on:input={event => (imagen = event.target.value) }
	/>

	<InputCustom 
		control="textarea"
		nombre="Descripcion"
		id="descripcion"
		placeholder="Descripcion"
		value={descripcion}
		on:input={event => (descripcion = event.target.value) }
	/>
	<button type="submit" class="btn btn-info" >Guardar</button>
</form>

</div>

