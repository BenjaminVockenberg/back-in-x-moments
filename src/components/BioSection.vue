<template>
<div class="container biog">    
    <div class="row align-items-center">
        <div class="col-sm-3">
            <img src="../assets/ben.jpg" alt="benjamin vockenberg">
        </div>
        <div class="col-sm-9">
            <h2>I'll be back...</h2>
            <p>...after spending some time with my daughter. Thank you <strong>Reservix GmbH</strong> for giving me the chance to take a parental leave of 4 month.</p>
            <p><strong>Special thx to:</strong> Helge Hollander, Katrin Stahlberg, Johannes Tolle, Katharina Junker, Benjamin Berg &amp; Carsten Müller</p>
            <p><strong>Thx to the team:</strong> Julia, Lea, Yook, Christian, Rafi, Ewgenij, Alexey, Andres, Dome, Matthias, Wiktor &amp; to all the other colleagues I missed!</p>
            <p>Best whishes Ben, Anne-Katrin &amp; Hannah-Marie</p>
        </div>
    </div>        
</div>
</template>

<script>
export default {
    name: 'BioSection'
}
</script>

<style scoped lang="scss">
img {
    width: 100%;
}

p {    
    font-size: 22px;
}

.biog {
    background-color: rgba(0,0,0, 0.5);
    padding: 2%;
}
</style>
