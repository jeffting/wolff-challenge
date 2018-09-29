<template>
    <div>
        <header class="win-header">Calculate your team</header>
        <span>Filter by</span>
        <b-dropdown id="ddown1" :text="filter" class="m-md-2">
            <b-dropdown-item @click="setDropdown('win')">Win</b-dropdown-item>
            <b-dropdown-item @click="setDropdown('option2')">Option 2</b-dropdown-item>
        </b-dropdown>
        <div class="flex-container">
            <div class="all-inputs-container">
            <section class="input-container">
                <b-form-checkbox id="checkbox1"
                        v-model="revenue.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="revenue.value"></b-form-input>
                <div class="input-title">Revenue</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox2"
                        v-model="spending.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="spending.value"></b-form-input>
                <div class="input-title">Spending</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox3"
                        v-model="recruit.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="recruit.value"></b-form-input>
                <div class="input-title">Average star of recruits</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox4"
                        v-model="ppg.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="ppg.value"></b-form-input>
                <div class="input-title">Points per game</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox5"
                        v-model="ppgA.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="ppgA.value"></b-form-input>
                <div class="input-title">Points per game allowed</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox9"
                        v-model="rank.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="rank.value"></b-form-input>
                <div class="input-title">Team Rank</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox6"
                        v-model="sos.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="sos.value"></b-form-input>
                <div class="input-title">Strength of schedule</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox7"
                        v-model="conference.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <!-- <b-form-input type="number" class="input-field" v-model="conference.value"></b-form-input> -->
                <b-dropdown id="down2" :text="conference.value" class="m-md-2 primary">
                    <b-dropdown-item @click="conference.value = 'SEC'">SEC</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'ACC'">ACC</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'PAC 12'">PAC 12</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'BIG 10'">BIG 10</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'BIG 12'">BIG 12</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'MWC'">Moutain West</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'Independent'">Independent</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'Sunbelt'">Sunbelt</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'MAC'">MAC</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'American'">American</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'CUSA'">CUSA</b-dropdown-item>


                </b-dropdown>
                <div class="input-title">Conference</div>
            </section>
            <section class="input-container">
                <b-form-checkbox id="checkbox8"
                        v-model="allAmericans.status"
                        value="true"
                        unchecked-value="false">
                </b-form-checkbox>
                <b-form-input type="number" class="input-field" v-model="allAmericans.value"></b-form-input>
                <div class="input-title">Number of All Americans</div>
            </section>
            <button class=" btn btn-primary" @click="calculateWin()">Calculate</button>
        </div>

            <div class="results-container">
                <div v-if="displayWinPercentage">
                    {{ winPercentage }}%
                </div>
                <div v-if="displayWinPercentage">Record ({{ gamesWon }}, {{ 13-gamesWon }})</div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            filter: "Win",
            displayWinPercentage: false,
            winPercentage: 0,
            revenue: {
                status: "true", value: 0, weight: -.000000000237, average: 24871249, hiddenVal: 0
            },
            spending: {
                status: 'true', value: 0, weight: .000000000124, average: 14254710, hiddenVal: 0
            },
            recruit: {
                status: "true", value: 0, weight: .0015893, average: 2.76, hiddenVal: 0
            },
            ppg: {
                status: "true", value: 0, weight: .0167049, average: 27.3, hiddenVal: 0
            },
            ppgA: {
                status: "true", value: 0, weight: -.0165219, average: 26.83, hiddenVal: 0
            },
            sos: {
                status: "true", value: 0, weight: -.001508, average: 75, hiddenVal: 0
            },
            conference: {
                status: "true", value: 'SEC', weight: -.0008677, average: 8.15, hiddenVal: 0
            },
            allAmericans: {
                status: "true", value: 0, weight: -.0013319, average: 0.1, hiddenVal: 0
            },
            rank: {
                status: "true", value: 0, weight: .0039645, average: 0, hiddenVal: 0
            },
            allObjects: [],
            gamesWon: 0
        }
    },
    created() {
    },
    methods: {
        calculateWin() {
            this.displayWinPercentage = true;
            this.getSelectedValues();
            this.runCalculations();
        },
        runCalculations() {
            this.allObjects.forEach(item => {
                item.value = item.value < 0 || item.value === "" ? 0 : item.value;
                if (item.status === "false") {
                    item.hiddenVal = item.average;
                } else {
                    item.hiddenVal = item.value;
                }
            });
            
            this.calcRank();
            this.calcSos();
            this.calcConf();
            let sum = .5000764; 
            this.allObjects.forEach(item => {
                sum = sum + (item.hiddenVal * item.weight);
            });
            sum = sum * 100;
            if (sum >= 100 ) {
                this.winPercentage = 100.0000;
            } else if (sum <= 0 ){
                this.winPercentage = 0.0000
            } else {
                this.winPercentage = sum.toFixed(4);
            }
            this.gamesWon = Math.round(this.winPercentage * 13 / 100);
            //a = (a-(a%1000))/1000;
        },
        calcSos() {
            this.sos.hiddenVal = (75 - this.sos.hiddenVal) / 3.75;
        },
        calcRank() {
         if (this.rank.value > 25) {
                this.rank.hiddenVal = 0;
                this.rank.value = 0;
            }
            if (this.rank.value !== 0) {
                this.rank.hiddenVal = 26-this.rank.value;
            } else {
                this.rank.hiddenVal = 0;
            }
        },
        calcConf() {
            if (this.conference.status === "true") {
                switch(this.conference.value) {
                    case 'SEC':
                        this.conference.hiddenVal = 13;
                        break;
                    case 'BIG 10':
                        this.conference.hiddenVal = 12;
                        break;
                    case 'MWC':
                        this.conference.hiddenVal = 6;
                        break;
                    case 'Independent':
                        this.conference.hiddenVal = 8;
                        break;
                    case 'BIG 12':
                        this.conference.hiddenVal = 10;
                        break;
                    case 'PAC 12':
                        this.conference.hiddenVal = 9;
                        break;
                    case 'ACC':
                        this.conference.hiddenVal = 11;
                        break;
                    case 'CUSA':
                        this.conference.hiddenVal = 4;
                        break;
                    case 'Sunbelt':
                        this.conference.hiddenVal = 1;
                        break;
                    case 'American':
                        this.conference.hiddenVal = 7;
                        break;
                    case 'MAC':
                        this.conference.hiddenVal = 5;
                        break;
                    default:
                        break;

                }
            }
        },
        getSelectedValues() {
            this.allObjects = [];
            this.allObjects.push(this.revenue);
            this.allObjects.push(this.spending);
            this.allObjects.push(this.recruit);
            this.allObjects.push(this.ppg);
            this.allObjects.push(this.ppgA);
            this.allObjects.push(this.sos);
            this.allObjects.push(this.conference);
            this.allObjects.push(this.allAmericans);
            this.allObjects.push(this.rank);
        },
        setDropdown(val) {
            if (val === 'win' ) {
                this.filter = "Win";
            } else if (val === 'option2') {
                this.filter = "Option 2";
            }
        }
    }
}
</script>
<style scoped>
.all-inputs-container {
    flex-grow: 1;
}
.results-container {
    flex-grow: 1;
    font-size: 50px;
    text-align: center;
}
.flex-container {
    display: flex;
    flex-direction: row;
    align-items: center;
}
.input-container {
    display: flex;
    flex-direction: row;
    align-items: center;
}
.input-field {
    margin-top: 10px;
    width: 120px;
    height: 30px;
}
.input-title {
    margin-left: 20px;
    font-size: 20px;
    padding-top: 5px;
}
button {
    margin-top: 10px;
    margin-left: 40px;
}
.win-header {
    text-align: center;
    font-size: 30px;
    margin-top: 40px;
    margin-bottom: 40px;
}
.cm-md-2 {
    color: blue;    
}
</style>