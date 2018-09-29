<template>
    <div>
        <div class="row-flex">
            <div><img class="football" src="https://i.pinimg.com/originals/70/6e/16/706e1673962f263dfdf865cc44f71101.png"/></div>
            <header class="big-header">Football Gurus</header>
        <div><img class="football" src="https://www.pngarts.com/files/3/American-Football-PNG-Image-With-Transparent-Background.png"/></div>
        </div>
        <h2 class="section-header">QUESTION</h2>
        <div class="text-container">
We wanted to know what it takes to achieve football excellence. How can we end the cycle of bad teams being bad and good teams being great? What will it take for your school to go undefeated and receive the impact that follows.        </div>

        <h2 class="section-header">PROCESS</h2>
        <div class="text-container">
            <ul>
                <li>Determined what factors were most important to a college football program's success.</li>
                <li>Gathered data using sportsreference.com, ESPN, and NCAA member school financials; we compiled the information into Excel.</li>
                <li>Using Tableau, we created visual analyses to understand the largest impact drivers on winning percentage.</li>
                <li>Developed a regression analysis through the use of Stata to predict winning percentage.</li>
                <li>Created an interactive website to accurately portray findings.</li>
            </ul>
        </div>
        <h2 class="section-header">IMPACT</h2>
        <div class="text-container">
            <ul>
                <li>Improve college enrollment</li>
                <li>Fund other academic and sports programs</li>
                <li>Become a top tier university</li>
            </ul>
        </div>
        <div class="img-container">
            <img src="https://www.saturdaydownsouth.com/wp-content/uploads/2016/01/Building-UT-Brick-by-MEME.jpg"/>
        </div>
    </div>
</template>
<script>
export default {

}
</script>
<style scoped>
h2 {
    font-size: 22px;
    font-weight: 700;
}
.big-header {
    font-size: 40px;
    margin-top: 20px;
    margin-bottom: 20px;
}
.text-container {
    font-size: 20px;
    margin-bottom: 30px;
    line-height: 2;
}
.img-container {
    text-align: center;
    margin-bottom: 50px;

}
.section-header {
    margin-top: 30px;
}
img {
    max-width: 50vw;
}
.football {
    width: 200px;
}
.row-flex {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>