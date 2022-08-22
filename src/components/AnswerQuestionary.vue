<template>
    
    <v-container >
        <v-card
            class="ma-auto"
            max-width="640"
        >
            <v-img
            src="https://cimg.cnyes.cool/prod/news/4938633/l/404eb1d37f09fa1d9f626ad80711ef1c.jpg"
            height="200px"
            ></v-img>

            <v-card-title>
                <strong>投資屬性分析</strong>
            </v-card-title>

            <v-card-subtitle>
            歡迎來到被動投資的世界！
            </v-card-subtitle>

            <v-card-actions>
            <v-form v-model="valid" ref="form">
                <v-container>
                <v-row>
                    <v-col
                    cols="12"
                    md="3"
                    >
                    <v-text-field
                        v-model="firstname"
                        :rules="nameRules"
                        :counter="1"
                        label="姓"
                        required
                        
                    ></v-text-field>
                    </v-col>

                    <v-col
                    cols="12"
                    md="3"
                    >
                    <v-text-field
                        v-model="lastname"
                        :rules="nameRules"
                        :counter="2"
                        label="名"
                        required
                    ></v-text-field>
                    </v-col>

                    <v-col
                    cols="12"
                    md="6"
                    >
                    <v-text-field
                        v-model="email"
                        :rules="emailRules"
                        label="E-mail"
                        required
                    ></v-text-field>
                    </v-col>

                    <v-col
                    cols="12"
                    md="6"
                    >
                        <v-btn
                            color="orange lighten-2"
                            text
                            @click="validate"
                        >
                            開始計算
                        </v-btn>
                    </v-col>
                </v-row>
                </v-container>
            </v-form>
            

            <v-spacer></v-spacer>

            <v-btn
                icon
                @click="show = !show"
            >
                <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
            </v-btn>
            </v-card-actions>

            <v-expand-transition>
            <div v-show="show">
                <v-divider></v-divider>

                <v-card-text>
                每個人都一定需要 <strong>退休金</strong> ，
                但你知道退休金要多少才夠嗎？
                <br><br>
                使用下方選單的投資試算功能，
                可以讓你清楚地知道自己需要存多少錢才能 <strong>安心退休</strong> 哦！
                <br><br>
                投資可以很簡單，您可以透過我們簡單每天透過 <strong>L I N E</strong> 規劃各種人生的夢想，想創業、想累積人生第一個百萬、想規劃孩子的教育金、想給老婆浪漫的蜜月回憶、想早點離開職場這些都有可能成真。
                </v-card-text>
            </div>
            </v-expand-transition>
        </v-card>

        <br>
        <v-expand-transition>
            <v-container 
            v-show="valid" 
            @click.left="cal_risk_free" 
            >
                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>請問您的教育程度（未成年客戶請選Ａ）</v-card-title>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                            <v-col
                            cols="12"
                            sm="6"
                            md="6"
                            >
                                <v-radio-group
                                v-model="qs[1]"
                                column
                                >
                                <v-radio
                                    label="國中以下"
                                    color="info"
                                    value="q1s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="高中（職）"
                                    color="success"
                                    value="q1s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="大學／專科"
                                    color="primary"
                                    value="q1s3"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="碩士"
                                    color="indigo"
                                    value="q1s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="博士"
                                    color="indigo darken-3"
                                    value="q1s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-col>
                            
                            </v-row>
                        </v-container>
                        </v-card-text>
                </v-card>
                
                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>是否有重大傷病證明</v-card-title>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                            <v-col
                            cols="12"
                            sm="6"
                            md="6"
                            >
                                <v-radio-group
                                v-model="qs[2]"
                                column
                                >
                                <v-radio
                                    label="是"
                                    color="error"
                                    value="q2s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="否"
                                    color="success"
                                    value="q2s2"
                                ></v-radio>
                                </v-radio-group>
                            </v-col>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>

                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>主要資金來源（複選題）</v-card-title>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                            <v-col
                                cols="12"
                                sm="4"
                                md="4"
                            >
                                <v-checkbox
                                v-model="q3"
                                label="薪資所得"
                                color="red"
                                value="q3s1"
                                hide-details
                                ></v-checkbox>
                                <v-checkbox
                                v-model="q3"
                                label="經營事業所得"
                                color="red darken-1"
                                value="q3s2"
                                hide-details
                                ></v-checkbox>
                                
                            </v-col>
                            <v-col
                                cols="12"
                                sm="4"
                                md="4"
                            >
                                <v-checkbox
                                v-model="q3"
                                label="投資所得"
                                color="indigo"
                                value="q3s3"
                                hide-details
                                ></v-checkbox>
                                <v-checkbox
                                v-model="q3"
                                label="買賣房地產"
                                color="indigo darken-3"
                                value="q3s4"
                                hide-details
                                ></v-checkbox>
                            </v-col>
                            <v-col
                                cols="12"
                                sm="4"
                                md="4"
                            >
                                <v-checkbox
                                v-model="q3"
                                label="退休年金"
                                color="orange"
                                value="q3s5"
                                hide-details
                                ></v-checkbox>
                                <v-checkbox
                                v-model="q3"
                                label="繼承與贈與"
                                color="orange darken-3"
                                value="q3s6"
                                hide-details
                                ></v-checkbox>
                                <v-checkbox
                                v-model="q3"
                                label="組金收入"
                                color="red darken-3"
                                value="q3s7"
                                hide-details
                                ></v-checkbox>
                            </v-col>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>
                
                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>針對您的投資組合，預期投資期限為多久</v-card-title>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                                <v-radio-group
                                v-model="qs[4]"
                                column
                                >
                                <v-radio
                                    label="未滿一年"
                                    color="error"
                                    value="q4s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="１～３"
                                    color="warning"
                                    value="q4s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="３～５"
                                    color="info"
                                    value="q4s3"
                                ></v-radio>
                                <br>                        
                                <v-radio
                                    label="５～７"
                                    color="success"
                                    value="q4s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="７以上"
                                    color="secondary"
                                    value="q4s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>

                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>我 ... 其他資金來源以滿足計劃外的現金需求。我 ... ...。</v-card-title>
                    <v-card-subtitle>以下哪個句子最能說明您在面對計劃外的大量現金需求時需要從該投資帳戶提款的情況？</v-card-subtitle>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                                <v-radio-group
                                v-model="qs[5]"
                                column
                                >
                                <v-radio
                                    label="沒有，需要從此帳戶進行提款"
                                    color="error"
                                    value="q5s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，需要從此帳戶進行大部分提款"
                                    color="warning"
                                    value="q5s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，需要從此帳戶進行部分提款"
                                    color="info"
                                    value="q5s3"
                                ></v-radio>
                                <br>                        
                                <v-radio
                                    label="還有，不太可能需要從此帳戶進行提款"
                                    color="success"
                                    value="q5s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，不需要從此帳戶進行提款"
                                    color="secondary"
                                    value="q5s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>

                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>個人/家庭年收入為(含薪資、租金、投資獲益等收入)</v-card-title>
                    <v-card-subtitle>
                        [備註]<br>此問題主要以個人收入為主。若您無個人收入, 則可依家庭收入回答此問題。
                    </v-card-subtitle>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                                <v-radio-group
                                v-model="qs[6]"
                                column
                                >
                                <v-radio
                                    label="沒有，需要從此帳戶進行提款"
                                    color="error"
                                    value="q6s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，需要從此帳戶進行大部分提款"
                                    color="warning"
                                    value="q6s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，需要從此帳戶進行部分提款"
                                    color="info"
                                    value="q6s3"
                                ></v-radio>
                                <br>                        
                                <v-radio
                                    label="還有，不太可能需要從此帳戶進行提款"
                                    color="success"
                                    value="q6s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="還有，不需要從此帳戶進行提款"
                                    color="secondary"
                                    value="q6s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>
                
                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>以下哪個句子最能描述您的財務狀況？<br>我的收入與資產、我的支出與負債，我有資金用於投資。</v-card-title>
                    <v-card-subtitle>
                        [定義]<br>
                        收入與資產：收入指薪資收入、租金收入、投資收入和其他等收入來源。<br>
                        此資產指流動性較佳之財產，並不包括不動產。支出與負債: 消費性支出與貸款。
                    </v-card-subtitle>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                            <v-col
                            cols="112"
                            sm="6"
                            md="6"
                            >
                                <v-radio-group
                                v-model="qs[7]"
                                column
                                >
                                <v-radio
                                    label="幾乎等於，極少量"
                                    color="error"
                                    value="q7s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="微幅超過，少量"
                                    color="warning"
                                    value="q7s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="超過，一些"
                                    color="info"
                                    value="q7s3"
                                ></v-radio>
                                <br>                        
                                <v-radio
                                    label="超過，足夠"
                                    color="success"
                                    value="q7s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="大幅超過，大量"
                                    color="secondary"
                                    value="q7s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-col>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>

                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>
                        您對金融商品的知識與理解是:<br>
                    </v-card-title>
                    <v-card-subtitle>
                        [定義]<br>
                        一般金融商品：股票、ETFs、債券、 投資型保險和基金等。<br>
                        進階金融商品：結構型商品、權證、選擇權、期貨、遠期合約等。<br>
                        [備註] 您所勾選的選項中的金融商品可能與實際投資的金融商品不同。<br>
                        [備註] 您所勾選的選項中的金融商品可能與實際投資的金融商品不同。<br>
                    </v-card-subtitle>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>

                            <v-radio-group
                            v-model="qs[8]"
                            column
                            >
                            <v-radio
                                label="對金融商品完全不了解,但想進一步理解"
                                color="error"
                                value="q8s1"
                            ></v-radio>
                            <br>
                            <v-radio
                                label="對一般的金融商品(不包括進階的金融商 品)的基本知識和理解有限"
                                color="warning"
                                value="q8s2"
                            ></v-radio>
                            <br>
                            <v-radio
                                label="對一般的金融商品(不包括進階的金融商 品)有基本的知識和理解"
                                color="info"
                                value="q8s3"
                            ></v-radio>
                            <br>                        
                            <v-radio
                                label="對一般的金融商品和進階的金融商品有一 些知識和理解"
                                color="success"
                                value="q8s4"
                            ></v-radio>
                            <br>
                            <v-radio
                                label="對一般的金融商品和進階的金融商品有豐 富的知識和理解"
                                color="secondary"
                                value="q8s5"
                            ></v-radio>
                            </v-radio-group>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>

                <br>

                <v-card 
                shaped
                class="ma-auto"
                max-width="640"
                >
                    <v-card-title>
                        請描述您的金融商品投資經驗:
                    </v-card-title>
                    <v-card-subtitle>
                        [備註]<br>您所勾選的選項中的金融商品可能與實際投資的金融商品不同。
                    </v-card-subtitle>
                    <v-card-text>
                        <v-container fluid>
                            <v-row>
                                <v-radio-group
                                v-model="qs[9]"
                                column
                                width="100%"
                                >
                                <v-radio
                                    label="除了存款(含活期存款及定期存款)，貨幣型基金以外,我在金融商品投資方面只有 有限的經驗"
                                    color="error"
                                    value="q9s1"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="我在金融商品投資方面擁有一些經驗，且只限於一般的金融商品"
                                    color="warning"
                                    value="q9s2"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="金融商品投資方面擁有相當的經驗，但只限於一般的金融商品"
                                    color="info"
                                    value="q9s3"
                                ></v-radio>
                                <br>                        
                                <v-radio
                                    label="我在金融商品投資方面擁有相當的經驗，包括一般的金融商品和進階的金融商品"
                                    color="success"
                                    value="q9s4"
                                ></v-radio>
                                <br>
                                <v-radio
                                    label="我在金融商品投資方面擁有豐富的經驗，包括一般的金融商品和進階的金融商品"
                                    color="secondary"
                                    value="q9s5"
                                ></v-radio>
                                </v-radio-group>
                            </v-row>
                        </v-container>
                    </v-card-text>
                </v-card>
            </v-container>
        </v-expand-transition>
        <v-container>

        <v-card 
        class="ma-auto"
        max-width="640"
        
        >
            <v-card-text>
            <v-container fluid>
                <v-row>
                <v-col>
                    無風險資產：
                    <v-progress-circular
                    :rotate="270"
                    :size="100"
                    :width="15"
                    :value="risk_free"
                    color="teal"
                    >
                    {{ risk_free }}
                    </v-progress-circular>
                </v-col>
                <v-col>
                    風險性資產：
                    <v-progress-circular
                    :rotate="-90"
                    :size="100"
                    :width="15"
                    :value="100 - risk_free"
                    color="red"
                    >
                    {{ 100 - risk_free }}
                    </v-progress-circular>
                </v-col>
                </v-row>

            </v-container>
            </v-card-text>
        </v-card>
        </v-container>
    </v-container>
    
</template>

<script>
  const jsonData = require('./../assets/questionNum.json'); 
  export default {
    data () {
      return {
        qs: ["", "", "", "", "", "", "", "", "", ""],
        q3: [],
        risk_free: 100,
        show: false,
        valid: false,
        firstname: '',
        lastname: '',
        nameRules: [
            v => !!v || 'required',
            v => v.length <= 2 || 'Name must be less than 2 characters',
        ],
        email: '',
        emailRules: [
            v => !!v || 'required',
            v => /.+@.+/.test(v) || 'E-mail must be valid',
        ],
      }
    },
    methods: {
      cal_risk_free () {
        let ans = [];
        
        this.q3.forEach(element => {
            if (element != ""){
                ans.push(jsonData[element])
            }
        })

        this.qs.forEach(element => {
            if (element != ""){
                ans.push(jsonData[element])
            }
        });

        let risk_free_pct = ans.reduce((a, b) => a + b, 0) / ans.length
        this.risk_free = 100 - Math.round(risk_free_pct)
      },
      validate () {
        this.$refs.form.validate()
        this.show = false
      },
    },
  }
</script>
