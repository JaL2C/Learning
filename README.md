<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>成本控制學習網站</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* 設定 Inter 字體 */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8; /* 淺灰色背景 */
            color: #334155; /* 深藍灰色文字 */
        }
        /* 自定義滾動條樣式 */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #e2e8f0;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #94a3b8;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #64748b;
        }
        /* Canvas 樣式 */
        #cvpChart {
            display: block;
            background-color: #fff;
            border-radius: 0.5rem;
            border: 1px solid #e2e8f0;
            margin-top: 1.5rem;
            width: 100%; /* Make canvas responsive */
            height: auto; /* Maintain aspect ratio */
        }
        .quiz-input {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid #cbd5e1;
            border-radius: 0.375rem;
            margin-top: 0.25rem;
            margin-bottom: 0.75rem;
        }
        .quiz-button {
            background-color: #3b82f6;
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        .quiz-button:hover {
            background-color: #2563eb;
        }
        .quiz-feedback {
            margin-top: 1rem;
            padding: 0.75rem;
            border-radius: 0.375rem;
            font-weight: bold;
        }
        .quiz-feedback.correct {
            background-color: #dcfce7;
            color: #16a34a;
        }
        .quiz-feedback.incorrect {
            background-color: #fee2e2;
            color: #dc2626;
        }
        .formula-display {
            font-size: 0.9rem;
            color: #4b5563;
            background-color: #e2e8f0;
            padding: 0.5rem;
            border-radius: 0.25rem;
            margin-top: 0.5rem;
            font-weight: normal;
            font-family: monospace;
        }
        .nav-link {
            padding: 0.5rem 1rem;
            border-radius: 0.375rem;
            transition: background-color 0.2s, color 0.2s;
        }
        .nav-link:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }
        /* Table specific styles */
        .acceptance-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1.5rem;
            margin-bottom: 1.5rem;
            /* Ensure table doesn't overflow on small screens */
            display: block; /* Allows overflow-x-auto to work */
            overflow-x: auto; /* Adds horizontal scroll if content is too wide */
            -webkit-overflow-scrolling: touch; /* Smooth scrolling on iOS */
        }
        .acceptance-table th, .acceptance-table td {
            border: 1px solid #cbd5e1;
            padding: 0.75rem;
            text-align: left;
            vertical-align: top;
        }
        .acceptance-table th {
            background-color: #e2e8f0;
            font-weight: bold;
            color: #475569;
            white-space: nowrap; /* Prevent header text from wrapping */
        }
        .acceptance-table td {
            white-space: normal; /* Allow content to wrap */
        }
        .acceptance-table tr:nth-child(even) {
            background-color: #f8fafc;
        }
        .acceptance-table ul {
            list-style: disc;
            padding-left: 1.25rem;
            margin-top: 0.5rem;
        }
        .acceptance-table ul li {
            margin-bottom: 0.25rem;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center py-8 px-4 sm:px-6 lg:px-8">
    <header class="w-full max-w-4xl bg-gradient-to-r from-blue-500 to-indigo-600 text-white p-6 rounded-lg shadow-xl mb-8 text-center">
        <h1 class="text-4xl font-extrabold tracking-tight sm:text-5xl lg:text-6xl">
            成本控制學習網站
        </h1>
        <p class="mt-4 text-xl sm:text-2xl font-light">
            深入學習成本控制與採購管理的核心概念及實務流程
        </p>
        <nav class="mt-6">
            <ul class="flex flex-col sm:flex-row justify-center space-y-2 sm:space-y-0 sm:space-x-4 text-base sm:text-lg font-medium">
                <li><a href="#cost-classification" class="nav-link">成本分類基礎</a></li>
                <li><a href="#key-formulas" class="nav-link">重要公式與計算</a></li>
                <li><a href="#quiz-section" class="nav-link">成本控制小測驗</a></li>
                <li><a href="#procurement-management" class="nav-link">採購管理實務</a></li>
            </ul>
        </nav>
    </header>

    <main class="w-full max-w-4xl bg-white p-6 rounded-lg shadow-lg">
        <section id="cost-classification" class="mb-8 p-6 bg-blue-50 rounded-lg border border-blue-200">
            <h2 class="text-3xl font-bold text-blue-700 mb-4 pb-2 border-b-2 border-blue-300">
                成本分類基礎
            </h2>
            <p class="text-base sm:text-lg leading-relaxed">
                在成本控制中，理解不同類型的成本是至關重要的第一步。它們在決策、預算和績效評估中扮演著不同的角色。以下我們將詳細探討固定成本、變動成本和半變動成本。
            </p>
        </section>

        <section id="fixed-costs" class="mb-8 p-6 bg-gray-50 rounded-lg border border-gray-200">
            <h2 class="text-2xl font-semibold text-gray-800 mb-4 pb-2 border-b border-gray-300">
                固定成本 (Fixed Costs)
            </h2>
            <div class="text-base sm:text-lg leading-relaxed">
                <p class="mb-4">
                    固定成本是指在一定相關範圍和一定時期內，其總額不隨業務量變動而變動的成本。即使業務量為零，固定成本也依然存在。然而，單位產品的固定成本會隨著業務量的增加而減少。
                </p>
                <p class="mb-4">
                    例如：廠房租金、機器設備的折舊費、管理人員的薪資、保險費等。這些費用無論生產多少產品，在一定時期內都是相對固定的。
                </p>
                <p class="font-medium text-gray-600">
                    <strong class="text-blue-500">提示：</strong> 老師上課時可能強調固定成本的「總額固定，單位變動」特性，以及其在短期決策中的非相關性。
                </p>
            </div>
        </section>

        <section id="variable-costs" class="mb-8 p-6 bg-green-50 rounded-lg border border-green-200">
            <h2 class="text-2xl font-semibold text-green-800 mb-4 pb-2 border-b border-green-300">
                變動成本 (Variable Costs)
            </h2>
            <div class="text-base sm:text-lg leading-relaxed">
                <p class="mb-4">
                    變動成本是指其總額隨業務量變動而呈同方向變動的成本，但單位產品的變動成本在一定相關範圍內保持不變。業務量增加，變動成本總額也增加；業務量減少，變動成本總額也減少。
                </p>
                <p class="mb-4">
                    例如：直接材料費、直接人工費（按件計酬）、產品包裝費、銷售佣金等。這些費用與生產或銷售的數量直接相關。
                </p>
                <p class="font-medium text-green-600">
                    <strong class="text-blue-500">提示：</strong> 老師上課時可能強調變動成本的「總額變動，單位固定」特性，以及其與邊際貢獻的關係。
                </p>
            </div>
        </section>

        <section id="semi-variable-costs" class="mb-8 p-6 bg-purple-50 rounded-lg border border-purple-200">
            <h2 class="text-2xl font-semibold text-purple-800 mb-4 pb-2 border-b border-purple-300">
                半變動成本 (Semi-Variable Costs / Mixed Costs)
            </h2>
            <div class="text-base sm:text-lg leading-relaxed">
                <p class="mb-4">
                    半變動成本（或稱混合成本）是指同時包含固定成本和變動成本性質的成本。它有一個固定的基礎部分，在此基礎上，隨著業務量的增加而增加。
                </p>
                <p class="mb-4">
                    例如：電話費（月租費是固定部分，通話費是變動部分）、水電費（基本費是固定部分，超額用量是變動部分）、設備維修費（定期檢修是固定，額外維修是變動）。
                </p>
                <p class="font-medium text-purple-600">
                    <strong class="text-blue-500">提示：</strong> 老師上課時可能會提到如何將半變動成本分解為固定和變動部分的方法（如高低點法、迴歸分析法）。
                </p>
            </div>
        </section>

        <section id="key-formulas" class="p-6 bg-yellow-50 rounded-lg border border-yellow-200">
            <h2 class="text-3xl font-bold text-yellow-700 mb-4 pb-2 border-b-2 border-yellow-300">
                重要公式與計算
            </h2>
            <div class="text-base sm:text-lg leading-relaxed">
                <p class="mb-4">
                    在成本控制中，理解並應用關鍵公式是進行分析和決策的基礎。以下是其中幾個核心的公式：
                </p>
                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-center font-bold text-xl text-yellow-800 mb-6">
                    <p class="mb-2">
                        利潤 = 收入 - 成本
                    </p>
                    <p class="text-base font-normal text-yellow-700">
                        這是企業經營的根本原則，表明了企業在一定時期內經營活動的最終成果。
                    </p>
                </div>

                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-center font-bold text-xl text-yellow-800 mb-6">
                    <p class="mb-2">
                        利潤 = (單位售價 × 銷售量) - (固定成本 + 變動成本)
                    </p>
                    <p class="text-base font-normal text-yellow-700">
                        此公式進一步細分了收入和成本，幫助我們更清晰地分析利潤的構成，是進行成本-數量-利潤 (CVP) 分析的基礎。
                    </p>
                </div>

                <h3 class="text-2xl font-semibold text-yellow-700 mb-3 pb-1 border-b border-yellow-300">
                    邊際貢獻：利潤的基石
                </h3>
                <p class="mb-4">
                    您提到的「當售價超過變動成本開始對固定成本產生貢獻可以回收固定成本」正是**邊際貢獻 (Contribution Margin)** 的核心概念。
                </p>
                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-center font-bold text-xl text-yellow-800 mb-6">
                    <p class="mb-2">
                        單位邊際貢獻 = 單位售價 - 單位變動成本
                    </p>
                    <p class="mb-2">
                        總邊際貢獻 = 總收入 - 總變動成本
                    </p>
                    <p class="text-base font-normal text-yellow-700">
                        邊際貢獻是每銷售一個單位產品所能產生的，用來彌補固定成本並創造利潤的金額。
                    </p>
                </div>
                <p class="mt-4">
                    當總邊際貢獻足以彌補所有固定成本時，企業達到損益平衡；超過固定成本的部分，即為企業的利潤。因此，邊際貢獻是分析產品獲利能力和進行短期決策（如是否接受特殊訂單、是否停產某產品）的重要指標。
                </p>

                <h3 class="text-2xl font-semibold text-yellow-700 mb-3 pb-1 border-b border-yellow-300">
                    成本比率：獲利能力的衡量
                </h3>
                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-center font-bold text-xl text-yellow-800 mb-6">
                    <p class="mb-2">
                        變動成本率 = 總變動成本 / 總收入
                    </p>
                    <p class="mb-2">
                        或：變動成本率 = 單位變動成本 / 單位售價
                    </p>
                    <p class="text-base font-normal text-yellow-700">
                        變動成本率表示每單位收入中有多少比例是變動成本。此比率越低，表示企業的變動成本控制得越好，或產品的毛利率越高。
                    </p>
                </div>
                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-center font-bold text-xl text-yellow-800">
                    <p class="mb-2">
                        邊際貢獻率 = 總邊際貢獻 / 總收入
                    </p>
                    <p class="mb-2">
                        或：邊際貢獻率 = 單位邊際貢獻 / 單位售價
                    </p>
                    <p class="text-base font-normal text-yellow-700">
                        邊際貢獻率表示每單位收入中有多少比例可以貢獻給固定成本和利潤。此比率越高，表示企業的獲利能力越強，也更容易達到損益平衡。
                    </p>
                </div>
                <p class="mt-4">
                    值得注意的是，變動成本率與邊際貢獻率之和為 1 (即 100%)。
                </p>

                <h3 class="text-2xl font-semibold text-yellow-700 mt-8 mb-3 pb-1 border-b border-yellow-300">
                    範例應用：牛肉麵店
                </h3>
                <div class="bg-yellow-100 p-4 rounded-md border border-yellow-300 text-yellow-800">
                    <p class="mb-2 font-bold">假設資料：</p>
                    <ul class="list-disc list-inside mb-4 ml-4">
                        <li>單位售價：120 元/碗</li>
                        <li>單位變動成本：36 元/碗</li>
                        <li>固定成本：16,800 元</li>
                    </ul>

                    <p class="mb-2 font-bold">計算：</p>
                    <div class="mb-4">
                        <p class="font-medium text-lg">1. 單位邊際貢獻：</p>
                        <p class="ml-4">單位邊際貢獻 = 單位售價 - 單位變動成本</p>
                        <p class="ml-4">單位邊際貢獻 = 120 元 - 36 元 = <span class="font-bold text-blue-700">84 元/碗</span></p>
                        <p class="mt-2 text-base text-yellow-700">
                            這表示每賣出一碗牛肉麵，就能為店裡貢獻 84 元來彌補固定成本。
                        </p>
                    </div>

                    <div class="mb-4">
                        <p class="font-medium text-lg">2. 損益平衡點 (單位數)：</p>
                        <p class="ml-4">損益平衡點 (單位數) = 固定成本 / 單位邊際貢獻</p>
                        <p class="ml-4">損益平衡點 (單位數) = 16,800 元 / 84 元/碗 = <span class="font-bold text-blue-700">200 碗</span></p>
                        <p class="mt-2 text-base text-yellow-700">
                            這表示牛肉麵店至少要賣出 200 碗牛肉麵，才能剛好彌補所有固定成本，達到不虧不賺的狀態。
                        </p>
                    </div>

                    <div class="mb-4">
                        <p class="font-medium text-lg">3. 變動成本率：</p>
                        <p class="ml-4">變動成本率 = 單位變動成本 / 單位售價</p>
                        <p class="ml-4">變動成本率 = 36 元 / 120 元 = <span class="font-bold text-blue-700">0.30 或 30%</span></p>
                        <p class="mt-2 text-base text-yellow-700">
                            這表示每 100 元的收入中，有 30 元是變動成本。
                        </p>
                    </div>

                    <div class="mt-4">
                        <p class="font-medium text-lg">4. 邊際貢獻率：</p>
                        <p class="ml-4">邊際貢獻率 = 單位邊際貢獻 / 單位售價</p>
                        <p class="ml-4">邊際貢獻率 = 84 元 / 120 元 = <span class="font-bold text-blue-700">0.70 或 70%</span></p>
                        <p class="mt-2 text-base text-yellow-700">
                            這表示每 100 元的收入中，有 70 元可以貢獻給固定成本和利潤。
                        </p>
                    </div>
                </div>
                <p class="mt-4">
                    透過這些比率，我們可以更全面地分析企業的成本結構和獲利能力。
                </p>

                <h3 class="text-2xl font-semibold text-yellow-700 mt-8 mb-3 pb-1 border-b border-yellow-300">
                    成本-數量-利潤 (CVP) 分析圖
                </h3>
                <p class="text-base sm:text-lg leading-relaxed mb-4">
                    此圖表視覺化呈現牛肉麵店的成本、收入與利潤關係，並標示損益平衡點，幫助您直觀理解各項要素的互動。
                </p>
                <canvas id="cvpChart"></canvas>
            </div>
        </section>

        <section id="quiz-section" class="mt-8 p-6 bg-blue-50 rounded-lg border border-blue-200">
            <h2 class="text-3xl font-bold text-blue-700 mb-4 pb-2 border-b-2 border-blue-300">
                成本控制小測驗
            </h2>
            <p class="text-base sm:text-lg leading-relaxed mb-6">
                現在，讓我們來練習一下！請根據以下咖啡店的數據，計算出各項指標。
            </p>

            <div class="bg-blue-100 p-4 rounded-md border border-blue-300 text-blue-800 mb-6">
                <p class="mb-2 font-bold">假設資料：</p>
                <ul class="list-disc list-inside mb-4 ml-4">
                    <li>單位售價：<span id="quizUnitPriceDisplay"></span> 元/杯</li>
                    <li>單位變動成本：<span id="quizUnitVariableCostDisplay"></span> 元/杯</li>
                    <li>實際銷售量：<span id="quizSalesVolumeDisplay"></span> 杯</li>
                    <li>實際利潤：<span id="quizActualProfitDisplay"></span> 元</li>
                </ul>
            </div>

            <div class="mb-4">
                <label for="quizUnitCM" class="block text-base sm:text-lg font-medium text-gray-700">1. 單位邊際貢獻 (元/杯)：</label>
                <input type="number" id="quizUnitCM" class="quiz-input" placeholder="請輸入您的答案">
            </div>

            <div class="mb-4">
                <label for="quizFixedCost" class="block text-base sm:text-lg font-medium text-gray-700">2. 固定成本 (元)：</label>
                <input type="number" id="quizFixedCost" class="quiz-input" placeholder="請輸入您的答案">
            </div>

            <div class="mb-4">
                <label for="quizBepUnits" class="block text-base sm:text-lg font-medium text-gray-700">3. 損益平衡點 (杯數)：</label>
                <input type="number" id="quizBepUnits" class="quiz-input" placeholder="請輸入您的答案">
            </div>

            <div class="mb-6">
                <label for="quizContributionMarginRatio" class="block text-base sm:text-lg font-medium text-gray-700">4. 邊際貢獻率 (請輸入小數，例如 0.75)：</label>
                <input type="number" step="0.01" id="quizContributionMarginRatio" class="quiz-input" placeholder="請輸入您的答案">
            </div>

            <div class="flex flex-col sm:flex-row space-y-2 sm:space-y-0 sm:space-x-4">
                <button id="checkQuizAnswers" class="quiz-button">檢查答案</button>
                <button id="refreshQuiz" class="quiz-button bg-gray-500 hover:bg-gray-600">刷新測驗</button>
            </div>

            <div id="quizFeedback" class="quiz-feedback hidden"></div>
        </section>

        <section id="procurement-management" class="mt-8 p-6 bg-indigo-50 rounded-lg border border-indigo-200">
            <h2 class="text-3xl font-bold text-indigo-700 mb-4 pb-2 border-b-2 border-indigo-300">
                採購管理實務
            </h2>
            <div class="text-base sm:text-lg leading-relaxed">
                <p class="mb-4">
                    採購管理是企業營運中至關重要的一環，它直接影響著成本、品質和供應鏈的效率。有效的採購管理不僅能降低成本，還能確保物料供應的穩定性，提升企業的整體競爭力。
                </p>
                <p class="mb-4">
                    主要目標包括：
                    <ul class="list-disc list-inside ml-4">
                        <li>確保物料供應的連續性。</li>
                        <li>以最低的總成本獲得所需物料。</li>
                        <li>保證物料的品質符合要求。</li>
                        <li>建立和維護良好的供應商關係。</li>
                        <li>提升採購流程的效率。</li>
                    </ul>
                </p>
                <p class="mb-4">
                    在成本控制的範疇內，採購管理扮演著源頭控制的角色。通過優化採購策略，例如批量採購、尋找替代供應商、談判議價等，可以直接影響變動成本（如原材料成本）和間接成本（如採購流程成本）。
                </p>

                <h3 class="text-2xl font-semibold text-indigo-700 mt-6 mb-3 pb-1 border-b border-indigo-300">
                    小額物品採購作業流程
                </h3>
                <p class="mb-4">
                    對於金額較小、頻繁發生的採購，企業通常會建立一套簡化的流程以提高效率，同時確保必要的控制。以下是小額物品採購的典型作業流程：
                </p>
                <ol class="list-decimal list-inside ml-4 space-y-2">
                    <li>
                        **請購與核准：**
                        <p class="ml-4">
                            請購部門提出請購需求後，需經部門 A 級主管核准。此步驟確保了採購的必要性和合理性。
                        </p>
                    </li>
                    <li>
                        **庫存確認：**
                        <p class="ml-4">
                            採購部門在接到請購單後，需確認所請購的物品是否為非倉庫的庫存品。這有助於避免重複採購和庫存積壓，有效控制成本。
                        </p>
                    </li>
                    <li>
                        **金額限制：**
                        <p class="ml-4">
                            採購金額必須在 3,000 元以下方可由採購部代為訂購。這是一個重要的控制點，確保小額採購的簡化流程不會被濫用，超出預算範圍。
                        </p>
                    </li>
                    <li>
                        **支付方式與週轉金：**
                        <p class="ml-4">
                            如果供應商送貨時需要支付現金，應以採購部的週轉金先行支付。週轉金是為了應對小額、緊急的現金支付需求而設立的。
                        </p>
                    </li>
                    <li>
                        **請款與補足週轉金：**
                        <p class="ml-4">
                            採購部需將第一聯（通常是請購單或驗收單）和發票向應付帳款組請款，以補足週轉金。這確保了資金的流動性和透明度，並完成了採購的財務閉環。
                        </p>
                    </li>
                </ol>
                <p class="mt-4 italic text-indigo-600">
                    此流程有助於平衡採購效率與內部控制，特別適用於日常辦公用品、維修零件等小額需求。
                </p>

                <h3 class="text-2xl font-semibold text-indigo-700 mt-6 mb-3 pb-1 border-b border-indigo-300">
                    採購部職責
                </h3>
                <p class="mb-4">
                    採購部門在企業中扮演著關鍵角色，其職責不僅限於執行採購，更涉及到成本控制、品質保障和供應鏈管理。以下是採購部的核心職責：
                </p>
                <ul class="list-disc list-inside ml-4 space-y-2">
                    <li>
                        **經濟採購量原則：**
                        <p class="ml-4">
                            採購人員應以訂購成本達到經濟採購量 (EOQ) 的原則進行採購。在符合此原則下，採購人員可建議以一次訂購固定數量、採分批交貨的方式進行採購，以降低存貨成本和倉儲風險。
                        </p>
                    </li>
                    <li>
                        **大宗採購與工程招標：**
                        <p class="ml-4">
                            對於大宗物品的採購和金額較大的裝修工程，應採取公開招標的方式。報價單需密封，以確保採購過程的公平、公正和透明，避免舞弊。
                        </p>
                    </li>
                    <li>
                        **合約審核：**
                        <p class="ml-4">
                            所有採購合約，特別是涉及重要金額或長期合作的合約，需要送到總公司法務室和法律顧問進行審核，以確保公司的權益受到保障，避免潛在的法律風險。
                        </p>
                    </li>
                    <li>
                        **本地採購優先原則：**
                        <p class="ml-4">
                            如果本地的工廠或供應商有能力製造或提供所需物品，應以本地選購為原則。這有助於支持本地經濟、縮短供應鏈、降低運輸成本，並便於溝通與協調。
                        </p>
                    </li>
                    <li>
                        **品質與規格驗證：**
                        <p class="ml-4">
                            如果商品無法用肉眼判斷其品質和規格（例如某些化學品、精密零件），應要求供應商在交貨時附上公證機構的檢驗報告書，以確保所採購物品符合標準。
                        </p>
                    </li>
                    <li>
                        **生財器具與設備保固：**
                        <p class="ml-4">
                            對於購買生財器具和設備，應要求承包商在交貨時提供產品保固證書，並載明售後服務的細節。這保障了設備的長期使用效益和維護權益。
                        </p>
                    </li>
                    <li>
                        **索賠事宜：**
                        <p class="ml-4">
                            如果訂單不符合約定或商品存在瑕疵，採購人員應向負責的供應商或保險公司辦理索賠事宜，以維護公司利益，減少損失。
                        </p>
                    </li>
                    <li>
                        **週轉金管理：**
                        <p class="ml-4">
                            週轉金是供急需使用，採購人員應妥善保管，不得擅自挪用。這強調了資金管理的紀律性和重要性，避免財務風險。
                        </p>
                    </li>
                </ul>
                <p class="mt-4 italic text-indigo-600">
                    這些職責共同確保了採購活動的規範性、經濟性和有效性，是企業成本控制不可或缺的一部分。
                </p>

                <h3 class="text-2xl font-semibold text-indigo-700 mt-6 mb-3 pb-1 border-b border-indigo-300">
                    生鮮食品、乾貨及雜貨類採購作業
                </h3>
                <p class="mb-4">
                    針對不同性質的採購物品，採購作業流程也會有所調整，以適應其市場特性和管理需求。
                </p>
                <ul class="list-disc list-inside ml-4 space-y-2">
                    <li>
                        **生鮮食品採購：**
                        <p class="ml-4">
                            由於生鮮食品市場價格每日變動，難以事先決定採購價格。因此，通常由採購人員、主廚及成本控制人員每週選定一天到市場訪價並做成紀錄。這有助於掌握市場動態，確保採購價格的合理性與競爭力。
                        </p>
                    </li>
                    <li>
                        **乾貨及雜貨類採購：**
                        <p class="ml-4">
                            乾貨及雜貨類物品的市場價格變動較少，因此通常以三個月為一期進行採購價格的評估或合約簽訂。這種方式有助於簡化採購流程，降低採購頻率和管理成本。
                        </p>
                    </li>
                </ul>
                <p class="mt-4 italic text-indigo-600">
                    靈活調整採購策略，是有效控制成本、確保供應品質的關鍵。
                </p>

                <h3 class="text-2xl font-semibold text-indigo-700 mt-6 mb-3 pb-1 border-b border-indigo-300">
                    採購貨品的驗收作業表
                </h3>
                <p class="mb-4">
                    所有採購物品都必須辦理驗收手續，以確保所收到的貨品符合訂單要求和品質標準。
                </p>
                <p class="font-bold text-base sm:text-lg mb-2">
                    (一) 驗收的程序
                </p>
                <ul class="list-decimal list-inside ml-4 space-y-1 mb-4 text-base sm:text-lg">
                    <li>驗收單位成立：公司可以成立一個專門的驗收單位，或指定相關部門人員負責驗收工作。</li>
                    <li>聯合驗收原則：原則上，驗收組應與採購部門共同辦理驗收手續。</li>
                    <li>驗收內容：驗收內容包括但不限於：數量清點、規格核對、品質檢查（外觀、包裝、效期等），並與相關文件進行比對。</li>
                </ul>

                <p class="font-bold text-base sm:text-lg mb-2">
                    (二) 各類別食品驗收程序細則
                </p>
                <table class="acceptance-table">
                    <thead>
                        <tr>
                            <th>類別</th>
                            <th>驗收標準</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td rowspan="3" class="font-bold">生鮮食品 (Fresh Food)</td>
                            <td>**肉類 (Meat)**
                                <ul>
                                    <li>色澤：需鮮明，不可以暗淡。</li>
                                    <li>肉質：應該有彈性，無異味。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td>**海鮮類 (Seafood)**
                                <ul>
                                    <li>魚鰓：需要鮮紅。</li>
                                    <li>魚眼：明亮。</li>
                                    <li>運送：運送時需要以冰塊覆蓋。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td>**蔬果類 (Vegetables & Fruits)**
                                <ul>
                                    <li>外觀：不可以有腐爛的現象。</li>
                                    <li>蟲害：不可以有蟲害。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td class="font-bold">冷凍食品 (Frozen Food)</td>
                            <td>
                                <ul>
                                    <li>解凍現象：不可以有解凍的現象。</li>
                                    <li>中心溫度：需要保持在 $-18^\circ C$ 以下。</li>
                                    <li>標示：需要清楚。</li>
                                    <li>保存期限：不可以超過一半。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td class="font-bold">冷藏食品 (Chilled Food)</td>
                            <td>
                                <ul>
                                    <li>食品顏色：不可以灰暗。</li>
                                    <li>中心溫度：需要維持在 $7^\circ C$ 以下。</li>
                                    <li>保存期限：不可以超過一半。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td class="font-bold">罐頭食品 (Canned Food)</td>
                            <td>
                                <ul>
                                    <li>鐵罐狀況：鐵罐不可以生鏽及凹凸。</li>
                                    <li>進口食品標籤：進口食品必須要有中文標籤。</li>
                                    <li>保存期限：不可以超過一半。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td rowspan="2" class="font-bold">其他類別 (Other Categories)</td>
                            <td>**調味料 (Seasonings)**
                                <ul>
                                    <li>潮濕：不可以潮濕。</li>
                                    <li>包裝：包裝需要完整。</li>
                                </ul>
                            </td>
                        </tr>
                        <tr>
                            <td>**蛋類 (Eggs)**
                                <ul>
                                    <li>髒物：不可以有髒物。</li>
                                </ul>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>
    </main>

    <footer class="w-full max-w-4xl text-center mt-8 p-4 text-gray-600 text-sm">
        <p>&copy; 2025 成本控制學習網站. All rights reserved.</p>
    </footer>

    <script>
        // CVP 圖表的 JavaScript 邏輯 (保持不變)
        window.onload = function() {
            const canvas = document.getElementById('cvpChart');
            if (!canvas) {
                console.error("Canvas element with ID 'cvpChart' not found.");
            } else {
                const ctx = canvas.getContext('2d');

                // 數據 (與牛肉麵範例一致)
                const unitPrice = 120;
                const unitVariableCost = 36;
                const fixedCost = 16800;

                // 計算 (與牛肉麵範例一致)
                const unitContributionMargin = unitPrice - unitVariableCost;
                const bepUnits = fixedCost / unitContributionMargin;
                const bepRevenue = bepUnits * unitPrice;

                // 圖表參數
                // 調整 padding 為響應式
                let padding;
                let chartWidth, chartHeight, xScale, yScale;

                const maxUnits = Math.ceil(bepUnits * 2.5 / 100) * 100;
                const maxRevenue = Math.ceil((unitPrice * maxUnits) / 10000) * 10000;

                function drawChart() {
                    ctx.clearRect(0, 0, canvas.width, canvas.height);
                    const containerWidth = canvas.parentElement.clientWidth;
                    canvas.width = containerWidth;
                    canvas.height = containerWidth * (2 / 3); // 維持 3:2 的比例

                    padding = canvas.width * 0.08; // 8% 的寬度作為 padding

                    chartWidth = canvas.width - 2 * padding;
                    chartHeight = canvas.height - 2 * padding;

                    xScale = chartWidth / maxUnits;
                    yScale = chartHeight / maxRevenue;

                    // 繪製座標軸
                    ctx.beginPath();
                    ctx.strokeStyle = '#334155';
                    ctx.lineWidth = 2;
                    ctx.moveTo(padding, padding);
                    ctx.lineTo(padding, canvas.height - padding);
                    ctx.lineTo(canvas.width - padding, canvas.height - padding);
                    ctx.stroke();

                    // 箭頭
                    ctx.fillStyle = '#334155';
                    ctx.beginPath();
                    ctx.moveTo(padding, padding);
                    ctx.lineTo(padding - 5, padding + 10);
                    ctx.lineTo(padding + 5, padding + 10);
                    ctx.fill();

                    ctx.beginPath();
                    ctx.moveTo(canvas.width - padding, canvas.height - padding);
                    ctx.lineTo(canvas.width - padding - 10, canvas.height - padding - 5);
                    ctx.lineTo(canvas.width - padding - 10, canvas.height - padding + 5);
                    ctx.fill();

                    // 座標軸標籤
                    ctx.font = '14px Inter'; // 調整字體大小
                    ctx.fillStyle = '#334155';
                    ctx.textAlign = 'center';
                    ctx.fillText('數量', canvas.width - padding / 2, canvas.height - padding / 2);
                    ctx.save();
                    ctx.translate(padding / 2, padding / 2);
                    ctx.rotate(-Math.PI / 2);
                    ctx.fillText('金額', 0, 0);
                    ctx.restore();

                    // 刻度標籤
                    ctx.font = '10px Inter'; // 調整字體大小
                    ctx.fillStyle = '#64748b';

                    for (let i = 0; i <= maxUnits; i += 50) {
                        const x = padding + i * xScale;
                        ctx.beginPath();
                        ctx.moveTo(x, canvas.height - padding);
                        ctx.lineTo(x, canvas.height - padding + 5);
                        ctx.stroke();
                        if (i !== 0) {
                            ctx.fillText(i, x, canvas.height - padding + 20);
                        }
                    }
                    for (let i = 0; i <= maxRevenue; i += 5000) {
                        const y = canvas.height - padding - i * yScale;
                        ctx.beginPath();
                        ctx.moveTo(padding, y);
                        ctx.lineTo(padding - 5, y);
                        ctx.stroke();
                        if (i !== 0) {
                            ctx.textAlign = 'right';
                            ctx.fillText(i, padding - 10, y + 4);
                        }
                    }
                    ctx.textAlign = 'center';

                    // 固定成本線
                    ctx.beginPath();
                    ctx.strokeStyle = '#ef4444';
                    ctx.lineWidth = 2;
                    const fcY = canvas.height - padding - fixedCost * yScale;
                    ctx.moveTo(padding, fcY);
                    ctx.lineTo(canvas.width - padding, fcY);
                    ctx.stroke();
                    ctx.fillStyle = '#ef4444';
                    ctx.fillText('固定成本 (FC)', padding + chartWidth / 2, fcY - 10);

                    // 收入線
                    ctx.beginPath();
                    ctx.strokeStyle = '#22c55e';
                    ctx.lineWidth = 2;
                    ctx.moveTo(padding, canvas.height - padding);
                    ctx.lineTo(padding + maxUnits * xScale, canvas.height - padding - (unitPrice * maxUnits) * yScale);
                    ctx.stroke();
                    ctx.fillStyle = '#22c55e';
                    ctx.fillText('收入', padding + maxUnits * xScale - 30, canvas.height - padding - (unitPrice * maxUnits) * yScale - 10);

                    // 總成本線
                    ctx.beginPath();
                    ctx.strokeStyle = '#f97316';
                    ctx.lineWidth = 2;
                    ctx.moveTo(padding, canvas.height - padding - fixedCost * yScale);
                    ctx.lineTo(padding + maxUnits * xScale, canvas.height - padding - (fixedCost + unitVariableCost * maxUnits) * yScale);
                    ctx.stroke();
                    ctx.fillStyle = '#f97316';
                    ctx.fillText('總成本', padding + maxUnits * xScale - 30, canvas.height - padding - (fixedCost + unitVariableCost * maxUnits) * yScale + 20);

                    // 損益平衡點
                    const bepX = padding + bepUnits * xScale;
                    const bepY = canvas.height - padding - bepRevenue * yScale;

                    ctx.beginPath();
                    ctx.strokeStyle = '#3b82f6';
                    ctx.lineWidth = 2;
                    ctx.setLineDash([5, 5]);
                    ctx.moveTo(bepX, canvas.height - padding);
                    ctx.lineTo(bepX, bepY);
                    ctx.moveTo(padding, bepY);
                    ctx.lineTo(bepX, bepY);
                    ctx.stroke();
                    ctx.setLineDash([]);

                    ctx.fillStyle = '#3b82f6';
                    ctx.beginPath();
                    ctx.arc(bepX, bepY, 5, 0, 2 * Math.PI);
                    ctx.fill();

                    ctx.font = '12px Inter'; // 調整字體大小
                    ctx.textAlign = 'left';
                    ctx.fillText(`BEP (${Math.round(bepUnits)} 碗, ${Math.round(bepRevenue)} 元)`, bepX + 10, bepY - 10);
                    ctx.textAlign = 'center';

                    // 利潤區
                    ctx.fillStyle = 'rgba(34, 197, 94, 0.1)';
                    ctx.beginPath();
                    ctx.moveTo(bepX, bepY);
                    ctx.lineTo(padding + maxUnits * xScale, canvas.height - padding - (unitPrice * maxUnits) * yScale);
                    ctx.lineTo(padding + maxUnits * xScale, canvas.height - padding - (fixedCost + unitVariableCost * maxUnits) * yScale);
                    ctx.closePath();
                    ctx.fill();
                    ctx.fillStyle = '#22c55e';
                    ctx.font = '10px Inter'; // 調整字體大小
                    ctx.fillText('利潤區', bepX + (maxUnits - bepUnits) * xScale / 2, bepY + (unitPrice * (maxUnits - bepUnits) - (fixedCost + unitVariableCost * maxUnits - bepRevenue)) * yScale / 2 - 20);

                    // 虧損區
                    ctx.fillStyle = 'rgba(239, 68, 68, 0.1)';
                    ctx.beginPath();
                    ctx.moveTo(padding, fcY);
                    ctx.lineTo(bepX, bepY);
                    ctx.lineTo(bepX, fcY);
                    ctx.closePath();
                    ctx.fill();
                    ctx.fillStyle = '#ef4444';
                    ctx.fillText('虧損區', padding + (bepX - padding) / 2, fcY + (bepY - fcY) / 2 + 20);
                }

                drawChart();
                window.addEventListener('resize', drawChart);
            }

            // 小測驗的 JavaScript 邏輯
            const quizUnitPriceDisplay = document.getElementById('quizUnitPriceDisplay');
            const quizUnitVariableCostDisplay = document.getElementById('quizUnitVariableCostDisplay');
            const quizSalesVolumeDisplay = document.getElementById('quizSalesVolumeDisplay');
            const quizActualProfitDisplay = document.getElementById('quizActualProfitDisplay');

            const quizUnitCMInput = document.getElementById('quizUnitCM');
            const quizFixedCostInput = document.getElementById('quizFixedCost');
            const quizBepUnitsInput = document.getElementById('quizBepUnits');
            const quizContributionMarginRatioInput = document.getElementById('quizContributionMarginRatio');
            const checkQuizAnswersButton = document.getElementById('checkQuizAnswers');
            const refreshQuizButton = document.getElementById('refreshQuiz');
            const quizFeedbackDiv = document.getElementById('quizFeedback');

            let currentQuizData = {};

            function generateNewQuizData() {
                const unitPrice = Math.floor(Math.random() * (250 - 80 + 1)) + 80;
                const unitVariableCost = Math.floor(Math.random() * (unitPrice - 30 - 20 + 1)) + 20;
                const unitContributionMargin = unitPrice - unitVariableCost;

                if (unitContributionMargin <= 0) {
                    return generateNewQuizData();
                }

                const fixedCost = Math.floor(Math.random() * (30000 - 8000 + 1)) + 8000;

                const bepUnits = fixedCost / unitContributionMargin;
                if (bepUnits < 50 || bepUnits > 500) {
                    return generateNewQuizData();
                }

                const salesVolumeLowerBound = Math.max(50, Math.floor(bepUnits * 0.7));
                const salesVolumeUpperBound = Math.ceil(bepUnits * 1.5);
                const salesVolume = Math.floor(Math.random() * (salesVolumeUpperBound - salesVolumeLowerBound + 1)) + salesVolumeLowerBound;

                const actualProfit = (unitPrice * salesVolume) - (unitVariableCost * salesVolume) - fixedCost;

                currentQuizData = {
                    unitPrice: unitPrice,
                    unitVariableCost: unitVariableCost,
                    salesVolume: salesVolume,
                    actualProfit: actualProfit,
                    correctUnitCM: unitContributionMargin,
                    correctFixedCost: fixedCost,
                    correctBepUnits: bepUnits,
                    correctContributionMarginRatio: unitContributionMargin / unitPrice
                };

                quizUnitPriceDisplay.textContent = unitPrice;
                quizUnitVariableCostDisplay.textContent = unitVariableCost;
                quizSalesVolumeDisplay.textContent = salesVolume;
                quizActualProfitDisplay.textContent = Math.round(actualProfit);

                quizUnitCMInput.value = '';
                quizFixedCostInput.value = '';
                quizBepUnitsInput.value = '';
                quizContributionMarginRatioInput.value = '';
                quizFeedbackDiv.classList.add('hidden');
                quizFeedbackDiv.innerHTML = '';
            }

            generateNewQuizData();
            refreshQuizButton.addEventListener('click', generateNewQuizData);

            checkQuizAnswersButton.addEventListener('click', function() {
                let allCorrect = true;
                let feedbackHtml = '您的答案：<br>';

                const userUnitCM = parseFloat(quizUnitCMInput.value);
                if (userUnitCM === currentQuizData.correctUnitCM) {
                    feedbackHtml += `1. 單位邊際貢獻：<span class="text-green-600">正確 (${currentQuizData.correctUnitCM})</span><br>`;
                } else {
                    feedbackHtml += `1. 單位邊際貢獻：<span class="text-red-600">錯誤！正確答案是 ${currentQuizData.correctUnitCM}</span><br>`;
                    feedbackHtml += `<div class="formula-display">公式：單位邊際貢獻 = 單位售價 - 單位變動成本</div>`;
                    allCorrect = false;
                }

                const userFixedCost = parseFloat(quizFixedCostInput.value);
                if (userFixedCost === currentQuizData.correctFixedCost) {
                    feedbackHtml += `2. 固定成本：<span class="text-green-600">正確 (${currentQuizData.correctFixedCost})</span><br>`;
                } else {
                    feedbackHtml += `2. 固定成本：<span class="text-red-600">錯誤！正確答案是 ${currentQuizData.correctFixedCost}</span><br>`;
                    feedbackHtml += `<div class="formula-display">公式：利潤 = (單位售價 × 銷售量) - (單位變動成本 × 銷售量) - 固定成本<br>因此，固定成本 = (單位售價 × 銷售量) - (單位變動成本 × 銷售量) - 利潤</div>`;
                    allCorrect = false;
                }

                const userBepUnits = parseFloat(quizBepUnitsInput.value);
                if (Math.round(userBepUnits) === Math.round(currentQuizData.correctBepUnits)) {
                    feedbackHtml += `3. 損益平衡點 (杯數)：<span class="text-green-600">正確 (${Math.round(currentQuizData.correctBepUnits)})</span><br>`;
                } else {
                    feedbackHtml += `3. 損益平衡點 (杯數)：<span class="text-red-600">錯誤！正確答案是 ${Math.round(currentQuizData.correctBepUnits)}</span><br>`;
                    feedbackHtml += `<div class="formula-display">公式：損益平衡點 (單位數) = 固定成本 / 單位邊際貢獻</div>`;
                    allCorrect = false;
                }

                const userContributionMarginRatio = parseFloat(quizContributionMarginRatioInput.value);
                if (Math.abs(userContributionMarginRatio - currentQuizData.correctContributionMarginRatio) < 0.001) {
                    feedbackHtml += `4. 邊際貢獻率：<span class="text-green-600">正確 (${currentQuizData.correctContributionMarginRatio.toFixed(2)})</span><br>`;
                } else {
                    feedbackHtml += `4. 邊際貢獻率：<span class="text-red-600">錯誤！正確答案是 ${currentQuizData.correctContributionMarginRatio.toFixed(2)}</span><br>`;
                    feedbackHtml += `<div class="formula-display">公式：邊際貢獻率 = 單位邊際貢獻 / 單位售價</div>`;
                    allCorrect = false;
                }

                quizFeedbackDiv.innerHTML = feedbackHtml;
                quizFeedbackDiv.classList.remove('hidden');
                if (allCorrect) {
                    quizFeedbackDiv.classList.remove('incorrect');
                    quizFeedbackDiv.classList.add('correct');
                } else {
                    quizFeedbackDiv.classList.remove('correct');
                    quizFeedbackDiv.classList.add('incorrect');
                }
            });
        };
    </script>
</body>
</html>
