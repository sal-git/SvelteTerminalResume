<script>
    import commandList from '../data/commands.json';
    export let command;
</script>
    
<section id="terminal__body">          
    <div id="terminal__prompt">            
        <span id="terminal__prompt--user">stephen@brownsville:</span>            
        <span id="terminal__prompt--location">~</span>            
        <span id="terminal__prompt--bling">$</span>
        <span id="terminal__prompt--output">{commandList[command]}</span>         
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
    #terminal__prompt--output {
        color: #fff;
        padding-left: 7px; 
    }
    #terminal__prompt {  
        display: flex;
    }
    #terminal__prompt--user {  
        color: #7eda28;
    }
    #terminal__prompt--location { 
        color: #4878c0;
    }
    #terminal__prompt--bling {  
        color: #dddddd;
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
</style>