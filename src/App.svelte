<script>
	import StdIn from './components/StdIn.svelte';
	import StdOut from './components/StdOut.svelte';

	let components = [{
		component: StdIn,
		props: {  }
	}];

	function handleCommand(event) {
		components = [...components, {component: StdOut, props: {command: event.detail.command.toLowerCase()}}, {component: StdIn, props: {}}]
	}

</script>

<main id="container">
	<div id="terminal" style="height: 65vh; overflow: auto;">
		<!-- Terminal Bar -->       
		<section id="terminal__bar">          
			<div id="bar__buttons">            
				<button class="bar__button" id="bar__button--exit">&#10005;</button>            
				<button class="bar__button">&#9472;</button>                
				<button class="bar__button">&#9723;</button>          
			</div>          
			<p id="bar__user">stephen@brownsville: ~</p>        
		</section>        
		<!-- Terminal Body -->
		<div>
			{#each components as component}
				<svelte:component this={component.component} on:command={handleCommand} { ...component.props }/>
			{/each}        
		</div>
	</div>    
</main>


<style>
	@import url('https://fonts.googleapis.com/css?family=Ubuntu');
	@import url('https://fonts.googleapis.com/css?family=Ubuntu+Mono'); 
	body {  
		background: linear-gradient(45deg, #57003f 0%,#f57453 100%); 
		font-family: Ubuntu;
		background-image: url("./images/brownsville_by_rogy_pro.jpg");
	} 
	#container {
		display: flex;  
		justify-content: center;  
		align-items: center;  
		height: 100vh;
		background-image: url("./images/brownsville_by_rogy_pro.jpg");
	} 
	#terminal {  
		border-radius: 12px;
		width: 70vw;  
		height: 65vh;  
		box-shadow: 2px 4px 10px rgba(0,0,0,0.5);
		background: rgba(56, 4, 40, 0.9);
	} 
	#terminal__bar {  
		display: flex;  
		width: 100%;  
		height: 30px;  
		align-items: center;  
		padding: 0 8px;  
		box-sizing: border-box;  
		border-top-left-radius: 5px;  
		border-top-right-radius: 5px;  
		background: linear-gradient(#504b45 0%,#3c3b37 100%);
	} 
	#bar__buttons {  
		display: flex;  
		align-items: center;
	} 
	.bar__button {  
		display: flex;  
		justify-content: center;  
		align-items: center;  
		padding: 0;  
		margin-right: 5px;  
		font-size: 8px;  
		height: 12px;  
		width: 12px;  
		box-sizing: border-box;  
		border: none;  
		border-radius: 100%;  
		background: linear-gradient(#7d7871 0%, #595953 100%);  
		text-shadow: 0px 1px 0px rgba(255,255,255,0.2);  
		box-shadow: 0px 0px 1px 0px #41403A, 0px 1px 1px 0px #474642;
	}
	.bar__button:hover {  
		cursor: pointer;
	}
	.bar__button:focus {  
		outline: none;
	}
	#bar__button--exit {  
		background: linear-gradient(#f37458 0%, #de4c12 100%);    
		background-clip: padding-box;
	} 
	#bar__user {   
		color: #d5d0ce;  
		margin-left: 6px;  
		font-size: 14px;  
		line-height: 15px;
	} 
</style>