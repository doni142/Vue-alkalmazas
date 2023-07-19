<script>
function toggle(){}
const valtozo = ref("walami")

function render(){
    const newH1 = document.createElement("h1");
    const newH1Content = document.createTextNode("Vue");
    newH1.appendChild(newH1Content);

    const newP = document.createElement("p");
    const newPContent = document.createTextNode("egy két há");
    newP.appendChild(newPContent);

    const a = document.createAttribute("class");
    a.value = valtozo;
    newP.setAttribute(a);
    newP.addEventListener('click', toggle);

    const newDiv = document.createElement("div");
    newDiv.appendChild(newH1);
    newDiv.appendChild(newP);

    const currentDiv = document.getElementById("div1");
    document.body.insertBefore(newDiv, currentDiv);
}

</script>

<template>


</template>
<style scoped></style>ą