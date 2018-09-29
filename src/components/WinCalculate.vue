<template>
    <div>
        <header class="win-header">It's all about the numbers</header>
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
                    <b-dropdown-item @click="conference.value = 'Mountain West'">Moutain West</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'Independent'">Independent</b-dropdown-item>
                    <b-dropdown-item @click="conference.value = 'WAC'">WAC</b-dropdown-item>
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
                status: "true", value: 0
            },
            spending: {
                status: 'true', value: 0
            },
            recruit: {
                status: "true", value: 0
            },
            ppg: {
                status: "true", value: 0
            },
            ppgA: {
                status: "true", value: 0
            },
            sos: {
                status: "true", value: 0
            },
            conference: {
                status: "true", value: 'SEC'
            },
            allAmericans: {
                status: "true", value: 0
            },
            selected: []
        }
    },
    created() {

    },
    methods: {
        calculateWin() {
            this.displayWinPercentage = true;
            this.getSelectedValues();
            this.selected.forEach(item => {
                item.value = item.value < 0 || item.value === "" ? 0 : item.value;
            })
        },
        getSelectedValues() {
            this.selected = [];
            if (this.revenue.status === 'true') {
                this.selected.push(this.revenue);
            }
            if (this.spending.status === 'true') {
                this.selected.push(this.spending);
            }
            if (this.recruit.status === 'true') {
                this.selected.push(this.recruit);
            }
            if (this.ppg.status === 'true') {
                this.selected.push(this.ppg);
            }
            if (this.ppgA.status === 'true') {
                this.selected.push(this.ppgA);
            }
            if (this.sos.status === 'true') {
                this.selected.push(this.sos);
            }
            if (this.conference.status === 'true') {
                this.selected.push(this.conference);
            }
            if (this.allAmericans.status === 'true') {
                this.selected.push(this.allAmericans);
            }
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