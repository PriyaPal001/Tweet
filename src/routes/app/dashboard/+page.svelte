<h1>Hello world!!!!!!!!</h1>
<div class="parent">
    <div class="div1 border-red-800 border"> 
        asfdc
    </div>
    <div class="div2 border-white border">
        asfef
     </div>
    </div>
<style>
    .parent {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: repeat(5, 1fr);
    grid-column-gap: 0px;
    grid-row-gap: 0px;
    }
    
    .div1 { grid-area: 1 / 1 / 6 / 3; }
    .div2 { grid-area: 1 / 3 / 6 / 8; }
</style>