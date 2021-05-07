<template>
    <div id="quiz-container"><img id="logo-crown" src="@/assets/logo.png" alt="headsUP Crown" />
        <div class="quiz-body">
            <div class="question">
                <p>What is the fastest animal in the planet ?</p>
            </div>
            <div id="timer" class="timer">
                <div class="base-timer"><svg class="base-timer__svg" viewBox="0 0 100 100"
                        xmlns="http://www.w3.org/2000/svg">
                        <g class="base-timer__circle">
                            <circle class="base-timer__path-elapsed" cx="50" cy="50" r="45" />
                        </g>
                    </svg><span id="base-timer-label" class="base-timer__label">{{time}}</span>
                </div>
            </div>

            <div class="options-container">
            <div class="option option-1">
                <div class="choice choice-1"><span class="choice-letter">A</span></div>
                <div class="choice-text">Turtle</div>
            </div>
            <div class="option option-2">
                <div class="choice choice-2"><span class="choice-letter">B</span></div>
                <div class="choice-text">Cheetah</div>
            </div>
            <div class="option option-3">
                <div class="choice choice-3"><span class="choice-letter">C</span></div>
                <div class="choice-text">Rabbit</div>
            </div>
            <div class="option option-4">
                <div class="choice choice-4"><span class="choice-letter">D</span></div>
                <div class="choice-text">Leopard</div>
            </div>
        </div>
        </div>
    </div>
</template>
<script>
    // import '../assets/js/main';

    // Start with an initial value of 20 seconds
    const TIME_LIMIT = 20;

    // Initially, no time has passed, but this will count up
    // and subtract from the TIME_LIMIT
    let timePassed = 0;
    let timeLeft = TIME_LIMIT;


    export default {

        name: "Quiz",
        data(){
        return{
            time:0
           }
        },
        methods: {
            onload() {
                this.showTimer();
            },
            formatTime(time) {
                // The largest round integer less than or equal to the result of time divided being by 60.
                const minutes = Math.floor(time / 60);
                
                // Seconds are the remainder of the time divided by 60 (modulus operator)
                let seconds = time % 60;
                
                // If the value of seconds is less than 10, then display seconds with a leading zero
                if (seconds < 10) {
                seconds = `0${seconds}`;
                }
            
                // The output in MM:SS format
                return `${minutes}:${seconds}`;
            },
            startTimer(){
               setInterval(() => {
                    timePassed = timePassed + 1;
                    timeLeft = TIME_LIMIT - timePassed;
                    this.time = this.formatTime(timeLeft);
                }, 1000);

                if(timeLeft == 0){
                    this.time = 20;
                }
            }
            
        },
        mounted: function(){
            this.startTimer()
        }
    }

    ;
</script>
<style scoped>
    #quiz-container {
        margin: 1rem auto;
        padding: 1rem;
        max-width: 750px;
    }

    .quiz-body {
        background-color: rgb(138, 43, 226, 0.7);
        width: 500px;
        height: 549px;
        border-radius: 15px;
        position: relative;
        left: 100px;
    }

    .question {
        color: white;
        font-weight: 700;
        display: flex;
        align-items: center;
        justify-content: center;
        position: inherit;
        top: 25px;
        font-size: 18px;
    }

    .options-container {
        position: relative;
        left: 133px;
        top: 32px;

    }

    .option {
        background-color: white;
        position: relative;
        width: 110px;
        height: 110px;
        border-radius: 8px;
    }

    .option-1 {
        top: 230px;
    }

    .option-2 {
        top: 121px;
        margin-left: 135px;
    }

    .option-3 {
        top: 153px;
    }

    .option-4 {
        top: 43px;
        margin-left: 135px;
    }

    .choice {
        border-radius: 50%;
        position: relative;
        top: 20px;
        width: 40px;
        height: 40px;
        margin: auto;
        text-align: center;
    }

    .choice-1 {
        background: rgb(255, 217, 0);
    }

    .choice-2 {
        background: rgb(143, 217, 241);
    }

    .choice-3 {
        background: rgb(168, 233, 151);
    }

    .choice-4 {
        background: rgb(228, 102, 86);
    }

    .choice-letter {
        color: white;
        font-weight: 700;
        position: relative;
        top: 8px;
    }

    .choice-text {
        font-weight: 700;
        text-align: center;
        position: relative;
        top: 25px;
    }

    #logo-headline {
        font-size: 3rem;
        padding: 0.5rem;
        color: #f50057;
        text-align: center;
    }

    .timer {
        position: absolute;
        left: 179px;
        top: 94px;
    }

    /* Sets the containers height and width */
    .base-timer {
        height: 150px;
        width: 150px;
    }

    /* Removes SVG styling that would hide the time label */
    .base-timer__circle {
        fill: none;
        stroke: none;
    }

    /* The SVG path that displays the timer's progress */
    .base-timer__path-elapsed {
        stroke-width: 7px;
        stroke: rgb(228, 68, 68);
    }

    .base-timer__label {
        position: absolute;
        color: white;
        width: 150px;
        height: 150px;
        top: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 48px;
        font-weight: 600;
    }

    #logo-crown {
        display: block;
        width: 40%;
        margin: 0 auto;
    }

    @media only screen and (max-width: 500px) {
        #logo-crown {
            width: 30%;
        }

        #logo-headline {
            font-size: 1.8rem;
        }
    }

    h1 {
        font-size: 1.3rem;
        padding: 0.7rem;
    }

    .divider {
        margin: 0.5rem 0;
        border: 3px solid rgba(102, 255, 166, 0.7);
        border-radius: 2px;
        box-shadow: 3px 5px 5px rgba(0, 0, 0, 0.3);
    }
</style>