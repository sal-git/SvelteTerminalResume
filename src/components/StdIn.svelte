<script>
    import { createEventDispatcher, onMount } from 'svelte';
    const dispatch = createEventDispatcher();

    let command;
    let disableInput = false;
    let help = ''

    function insertCommand() {
        dispatch('command', {
            command: command
        });
    }

    const handleKeyup = () => {
        if (event.code == 'Enter') {
            event.preventDefault();
            insertCommand();
            disableInput = true;
        }
    }

    onMount(() => {
        setTimeout(function(){ help = 'Type Help' }, 3000);
    });

</script>

<section id="terminal__body">          
    <div id="terminal__prompt">            
        <span id="terminal__prompt--user">stephen@brownsville:</span>            
        <span id="terminal__prompt--location">~</span>            
        <span id="terminal__prompt--bling">$</span>
        <input placeholder={help} type="text" class="input" bind:value={command} on:keyup|preventDefault={handleKeyup} disabled={disableInput} autofocus>         
    </div>        
</section>

<style>
    #terminal__body {  
        font-family: 'Ubuntu Mono';  
        height: calc(100% - 30px);  
        padding-top: 2px;  
        margin-top: -1px;
        padding-left: 6px;
    } 
    #terminal__prompt {  
        display: flex;
        margin: auto;
        padding-top: 8px;
    }
    #terminal__prompt--user {  
        color: #7eda28;
        padding-top: 6px;
    }
    #terminal__prompt--location { 
        color: #4878c0;
        padding-top: 6px;
    }
    #terminal__prompt--bling {  
        color: #dddddd;
        padding-top: 6px;
    }
    #terminal__prompt--cursor {  
        display: block;  
        height: 17px;  
        width: 8px;  
        margin-left: 9px;  
        animation: blink 1200ms linear infinite;
    } 
    @keyframes blink {  
        0% {    
            background: #ffffff;  
        }  
        49% {    
            background: #ffffff;  
        }  
        60% {    
            background: transparent;  
        }  
        99% {    
            background: transparent;  
        }  100% {    
            background: #ffffff;  
        }
    } 
    @media (max-width: 600px) {  
        #terminal {    
            max-height: 90%;    
            width: 90%;  
        }
    }
    .input:focus {
        background: transparent;
        border-color: transparent;
        outline: none;
        color: #fff;
        caret-color: auto;
    }
    .input:disabled {
        background: transparent;
        border-color: transparent;
        outline: none;
        color: #fff
    }
    .input {
        background: transparent;
        border-color: transparent;
        outline: none;
        color: #fff
    }
</style>