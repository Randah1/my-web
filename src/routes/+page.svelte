<script lang="ts">

import SquareRoot from'$lib/icons/Squareroot.svelte';
import BackSpace from'$lib/icons/BackSpace.svelte';

let equation: string="";

function addToEquation (value:string)
{
    equation +=value;
}

function restart()
{
    equation="";
}
function backspace()
{
    switch(equation.substring(equation.length - 3 , equation.length ))
    {
        case " * ":
        case " + ":
        case " - ":
        case " / ":
        equation=equation.substring(0,equation.length-3);
       break;
    
      break;
        default:
        equation=equation.substring(0,equation.length-1);

    }
  
}

function solve()
{
equation = eval(equation);

}
</script>

<svelte:head>
    <title>
         آلة حاسبة
    </title>
</svelte:head>

<div 
   class="bg-[#f4f1f8] h-fit w-fit rounded-3xl grid grid-cols-4 gap-3 p-3 font-semibold 
 text-[#686f79] text-xl shadow-xl shadow-[rgb(139,148,167)]  ">
   <!--TODO fix overflowing numbers -->
 <div class="bg-blue-300 rounded-full col-span-4 h-12 flex items-center px-4 mb-2 text-white 
    shadow-md shadow-[rgb(162,169,184)] ">
    {equation}
 </div>
          
         <!--<button class="bg-[#f3f6fc] hover:bg-[#eceef3]"><SquareRoot />   </button> هذا لما كنت حاطة ازرار الجذر-->   
    
         <!--row1-->
         <button on:click={restart} class="bg-[#f3f6fc] hover:bg-[#eceef3]">AC</button>
        <button on:click={backspace} class="bg-[#f3f6fc] hover:bg-[#eceef3]">
                <BackSpace/>
            </button>
        <button on:click={()=>addToEquation ('/100')} class="bg-[#f3f6fc]  hover:bg-[#eceef3]">%</button>
        <button on:click={()=>addToEquation (' + ')} class="bg-blue-800 text-white  hover:bg-blue-800/80">+</button>
           
        <!--row2-->
        
            <button on:click={()=>addToEquation ('7')}>7</button>
           
            <button on:click={()=>addToEquation ('8')}>8</button>
            <button on:click={()=>addToEquation ('9')}>9</button>
            <button on:click={()=>addToEquation (' - ')} class="bg-blue-700 text-white  hover:bg-blue-700/80">-</button>
        
            <button on:click={()=>addToEquation ('4')}>4</button>
            <button on:click={()=>addToEquation ('5')}>5</button>
            <button on:click={()=>addToEquation ('6')}>6</button>
            <button on:click={()=>addToEquation (' / ')} class="bg-blue-600 text-white  hover:bg-blue-600/80">/</button>
        
            <button on:click={()=>addToEquation ('1')}>1</button>
            <button on:click={()=>addToEquation ('2')}>2</button>
            <button on:click={()=>addToEquation ('3')}>3</button>
            <button on:click={()=>addToEquation (' * ')} class="bg-blue-500 text-white  hover:bg-blue-500/80">X</button>
        
            <button on:click={()=>addToEquation ('.')}>.</button> 
            <button on:click={()=>addToEquation ('0')}>0</button>
            <button on:click={ solve } class="col-span-2 w-full">=</button>
          
        
        
    
    
</div>




