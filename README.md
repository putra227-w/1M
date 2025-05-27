<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wealth Building Tracking System</title>
    <link rel="manifest" href="/manifest.json">
    <style>
        /* Reset CSS */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        /* Body Styling - Dark Theme */
        body {
            font-family: 'Inter', sans-serif; /* Changed font to Inter for modern feel */
            line-height: 1.6;
            color: #e0e0e0; /* Light grey text for dark background */
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); /* Dark blue gradient */
            min-height: 100vh;
            padding: 20px;
        }
        
        /* Main Container */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: #1f2842; /* Slightly lighter dark blue for container */
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3); /* Darker shadow */
            overflow: hidden;
        }
        
        /* Header Section */
        .header {
            background: linear-gradient(135deg, #0f4c75 0%, #3282b8 100%); /* Blue gradient for header */
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 300;
        }
        
        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }
        
        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            background: #16213e; /* Darker background for tabs */
            border-bottom: 2px solid #0f4c75; /* Blue border */
            flex-wrap: wrap; /* Allow tabs to wrap on smaller screens */
        }
        
        .nav-tab {
            flex: 1;
            padding: 15px 20px;
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1em;
            font-weight: 600;
            color: #a0a0a0; /* Lighter grey for inactive tabs */
            transition: all 0.3s ease;
            position: relative;
            min-width: 120px; /* Ensure tabs don't get too small */
        }
        
        .nav-tab:hover {
            background: #1f2842; /* Slightly lighter dark blue on hover */
            color: #ffffff; /* White text on hover */
        }
        
        .nav-tab.active {
            background: #1f2842; /* Container background for active tab */
            color: #3282b8; /* Bright blue for active tab */
            border-bottom: 3px solid #3282b8; /* Bright blue indicator */
        }
        
        /* Tab Content Sections */
        .tab-content {
            display: none;
            padding: 30px;
            animation: fadeIn 0.3s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Section Styling */
        .section {
            margin-bottom: 40px;
            background: #2a3857; /* Darker blue for sections */
            border-radius: 10px;
            padding: 25px;
            border-left: 5px solid #3282b8; /* Blue accent border */
        }
        
        .section h3 {
            color: #ffffff; /* White text for section titles */
            margin-bottom: 20px;
            font-size: 1.4em;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .icon {
            font-size: 1.2em;
            color: #3282b8; /* Blue icon color */
        }

        /* Responsive Table Wrapper */
        .table-responsive {
            overflow-x: auto; /* Allows horizontal scrolling for tables */
            -webkit-overflow-scrolling: touch; /* Smooth scrolling on iOS */
            margin-bottom: 20px;
        }
        
        table {
            width: 100%; /* Ensure table takes full width of its container */
            min-width: 700px; /* Minimum width to prevent content from collapsing too much */
            border-collapse: collapse;
            background: #1f2842; /* Dark background for tables */
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #3a4768; /* Slightly lighter border for dark theme */
            white-space: nowrap; /* Prevent text wrapping in table cells */
            color: #e0e0e0; /* Light text for table cells */
        }
        
        th {
            background: linear-gradient(135deg, #0f4c75 0%, #3282b8 100%); /* Blue gradient for table headers */
            color: white;
            font-weight: 600;
            font-size: 0.9em;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        tr:hover {
            background: #2a3857; /* Darker blue on row hover */
        }
        
        /* Form Input Styling */
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 2px solid #3a4768; /* Darker border for inputs */
            border-radius: 5px;
            font-size: 0.9em;
            transition: border-color 0.3s ease;
            background-color: #1f2842; /* Dark background for inputs */
            color: #e0e0e0; /* Light text for inputs */
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #3282b8; /* Bright blue on focus */
            box-shadow: 0 0 0 3px rgba(50, 130, 184, 0.3); /* Blue shadow on focus */
        }
        
        /* Button Styling */
        .btn {
            background: linear-gradient(135deg, #3282b8, #0f4c75); /* Blue gradient for buttons */
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            margin: 5px;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(50, 130, 184, 0.3); /* Blue shadow on hover */
        }
        
        .btn-success {
            background: linear-gradient(135deg, #28a745, #218838); /* Green for success */
        }
        
        .btn-danger {
            background: linear-gradient(135deg, #dc3545, #c82333); /* Red for danger */
        }
        
        /* Summary Cards */
        .summary-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background: #2a3857; /* Darker blue for cards */
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2); /* Darker shadow for cards */
            text-align: center;
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .card h4 {
            color: #ffffff; /* White text for card titles */
            margin-bottom: 10px;
            font-size: 1.1em;
        }
        
        .card .value {
            font-size: 2em;
            font-weight: bold;
            color: #3282b8; /* Bright blue for values */
            margin-bottom: 5px;
        }
        
        .card .target {
            font-size: 0.9em;
            color: #a0a0a0; /* Light grey for target text */
        }
        
        /* Progress Bar */
        .progress-bar {
            background: #3a4768; /* Darker background for progress bar */
            border-radius: 10px;
            height: 8px;
            margin: 10px 0;
            overflow: hidden;
        }
        
        .progress-fill {
            background: linear-gradient(90deg, #3282b8, #0f4c75); /* Blue gradient for progress fill */
            height: 100%;
            transition: width 0.3s ease;
        }
        
        /* Notes/Tips */
        .note {
            background: #2a3857; /* Dark background for notes */
            color: #856404; /* Keep original warning color, but ensure contrast */
            padding: 15px;
            border-radius: 5px;
            border-left: 4px solid #ffc107; /* Yellow border */
            margin: 20px 0;
            font-size: 0.9em;
        }
        
        .note.success {
            background: #2a3857; /* Dark background for success notes */
            color: #3282b8; /* Blue text for success notes */
            border-left-color: #3282b8; /* Blue border */
        }

        /* Custom Message Box */
        .message-box {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #3282b8; /* Blue for success messages */
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            min-width: 300px;
            animation: slideIn 0.5s forwards;
        }

        .message-box.error {
            background-color: #dc3545; /* Red for error messages */
        }

        .message-box .close-btn {
            background: none;
            border: none;
            color: white;
            font-size: 1.5em;
            cursor: pointer;
            margin-left: 15px;
        }

        @keyframes slideIn {
            from { top: -50px; opacity: 0; }
            to { top: 20px; opacity: 1; }
        }
        
        /* Chart specific styling */
        .chart-container {
            background: #1f2842;
            border-radius: 10px;
            padding: 20px;
            margin-top: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        /* Added height to canvas for better chart rendering */
        .chart-container canvas {
            max-height: 350px; /* Limits the maximum height of the chart */
        }

        /* Responsive Design for smaller screens */
        @media (max-width: 768px) {
            body {
                padding: 10px; /* Reduce overall padding on small screens */
            }
            .container {
                margin: 0; /* Remove side margins */
                border-radius: 0; /* Make it full width */
                box-shadow: none; /* Remove shadow to blend with body */
            }
            
            .header {
                padding: 20px;
            }
            
            .header h1 {
                font-size: 1.8em; /* Smaller font for title */
            }
            
            .header p {
                font-size: 1em; /* Smaller font for subtitle */
            }

            .nav-tabs {
                flex-direction: column; /* Stack tabs vertically */
                border-bottom: none; /* Remove bottom border if stacked */
            }

            .nav-tab {
                border-bottom: 1px solid #0f4c75; /* Add border between stacked tabs */
                border-radius: 0; /* Remove rounded corners for stacked tabs */
                min-width: unset; /* Remove min-width for stacked tabs */
                width: 100%; /* Make tabs take full width */
            }

            .nav-tab.active {
                border-bottom: 3px solid #3282b8; /* Keep active indicator */
            }
            
            .tab-content {
                padding: 15px; /* Reduce padding inside tab content */
            }
            
            .section {
                padding: 15px; /* Reduce section padding */
            }

            .section h3 {
                font-size: 1.2em; /* Smaller section titles */
            }

            table {
                font-size: 0.8em; /* Smaller font for table content */
            }
            
            .summary-cards {
                grid-template-columns: 1fr; /* Stack cards vertically */
            }

            .card {
                padding: 20px; /* Adjust card padding */
            }

            .card .value {
                font-size: 1.8em; /* Smaller value font */
            }
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>💰 Wealth Building Tracker</h1>
            <p>Your journey to Rp 1.16 Billion in 6 years</p>
        </div>
        
        <div id="messageBox" class="message-box" style="display:none;">
            <span id="messageText"></span>
            <button class="close-btn" onclick="document.getElementById('messageBox').style.display='none';">&times;</button>
        </div>

        <div class="nav-tabs">
            <button class="nav-tab active" onclick="showTab('dashboard')">📊 Dashboard</button>
            <button class="nav-tab" onclick="showTab('income')">💼 Income Tracker</button>
            <button class="nav-tab" onclick="showTab('expenses')">💸 Expenses</button>
            <button class="nav-tab" onclick="showTab('investments')">📈 Investments</button>
            <button class="nav-tab" onclick="showTab('learning')">🎓 Learning</button>
            <button class="nav-tab" onclick="showTab('assets')">🏠 Assets</button>
            <button class="nav-tab" onclick="showTab('goals')">🎯 Goals</button>
        </div>
        
        <div id="dashboard" class="tab-content active">
            <div class="summary-cards">
                <div class="card">
                    <h4>Current Net Worth</h4>
                    <div class="value" id="totalNetWorth">Rp 0</div>
                    <div class="target">Target: Rp 1.16B</div>
                    <div class="progress-bar">
                        <div class="progress-fill" id="netWorthProgress" style="width: 0%"></div>
                    </div>
                </div>
                <div class="card">
                    <h4>Monthly Income</h4>
                    <div class="value" id="monthlyIncome">Rp 0</div>
                    <div class="target">Target: Rp 50M+</div>
                </div>
                <div class="card">
                    <h4>Savings Rate</h4>
                    <div class="value" id="savingsRate">0%</div>
                    <div class="target">Target: 50-70%</div>
                </div>
                <div class="card">
                    <h4>Investment Returns</h4>
                    <div class="value" id="investmentReturns">0%</div>
                    <div class="target">Target: 20%+</div>
                </div>
            </div>
            
            <div class="note success">
                <strong>💡 Quick Start:</strong> Mulai dengan mengisi Income Tracker untuk data entry/admin work yang sudah didapat!
            </div>
        </div>
        
        <div id="income" class="tab-content">
            <div class="section">
                <h3><span class="icon">💼</span>Income Streams</h3>
                <div class="table-responsive">
                    <table id="incomeTable">
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Source</th>
                                <th>Type</th>
                                <th>Client</th>
                                <th>Amount (Rp)</th>
                                <th>Hours</th>
                                <th>Rate/Hour</th>
                                <th>Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><input type="date" id="incomeDate"></td>
                                <td><input type="text" id="incomeSource" placeholder="e.g., Freelance Project X"></td> <td>
                                    <select id="incomeType">
                                        <option>Project</option>
                                        <option>Hourly</option>
                                        <option>Retainer</option>
                                        <option>Commission</option>
                                    </select>
                                </td>
                                <td><input type="text" id="clientName" placeholder="Client name"></td>
                                <td><input type="number" id="incomeAmount" placeholder="0"></td>
                                <td><input type="number" id="incomeHours" placeholder="0"></td>
                                <td><input type="number" id="incomeRate" placeholder="0" readonly></td>
                                <td>
                                    <select id="incomeStatus">
                                        <option>Pending</option>
                                        <option>Paid</option>
                                        <option>Overdue</option>
                                    </select>
                                </td>
                                <td><button class="btn" onclick="addIncome()">Add</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="note">
                    <strong>📝 Tips:</strong> Track setiap income stream untuk melihat mana yang paling profitable. Focus pada client dan project type yang memberikan ROI tertinggi.
                </div>

                <div class="chart-container">
                    <h3>Grafik Pendapatan Bulanan</h3>
                    <canvas id="monthlyIncomeChart"></canvas>
                </div>
            </div>
        </div>
        
        <div id="expenses" class="tab-content">
            <div class="section">
                <h3><span class="icon">💸</span>Monthly Expenses Breakdown</h3>
                <div class="table-responsive">
                    <table id="expensesTable">
                        <thead>
                            <tr>
                                <th>Category</th>
                                <th>Budgeted (Rp)</th>
                                <th>Actual (Rp)</th>
                                <th>New Expense (Rp)</th>
                                <th>Difference</th>
                                <th>% of Income</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Living Expenses</td>
                                <td><input type="number" id="livingBudget" placeholder="0"></td>
                                <td><input type="number" id="livingActual" placeholder="0" readonly></td>
                                <td><input type="number" id="newLivingExpense" placeholder="0"></td>
                                <td id="livingDiff">Rp 0</td>
                                <td id="livingPercent">0%</td>
                                <td><button class="btn btn-success" onclick="recordNewExpense('living')">Add</button></td>
                            </tr>
                            <tr>
                                <td>Tools & Software</td>
                                <td><input type="number" id="toolsBudget" placeholder="0"></td>
                                <td><input type="number" id="toolsActual" placeholder="0" readonly></td>
                                <td><input type="number" id="newToolsExpense" placeholder="0"></td>
                                <td id="toolsDiff">Rp 0</td>
                                <td id="toolsPercent">0%</td>
                                <td><button class="btn btn-success" onclick="recordNewExpense('tools')">Add</button></td>
                            </tr>
                            <tr>
                                <td>Learning & Courses</td>
                                <td><input type="number" id="learningBudget" placeholder="0"></td>
                                <td><input type="number" id="learningActual" placeholder="0" readonly></td>
                                <td><input type="number" id="newLearningExpense" placeholder="0"></td>
                                <td id="learningDiff">Rp 0</td>
                                <td id="learningPercent">0%</td>
                                <td><button class="btn btn-success" onclick="recordNewExpense('learning')">Add</button></td>
                            </tr>
                            <tr>
                                <td>Marketing & Business</td>
                                <td><input type="number" id="marketingBudget" placeholder="0"></td>
                                <td><input type="number" id="marketingActual" placeholder="0" readonly></td>
                                <td><input type="number" id="newMarketingExpense" placeholder="0"></td>
                                <td id="marketingDiff">Rp 0</td>
                                <td id="marketingPercent">0%</td>
                                <td><button class="btn btn-success" onclick="recordNewExpense('marketing')">Add</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="summary-cards">
                    <div class="card">
                        <h4>Total Expenses</h4>
                        <div class="value" id="totalExpenses">Rp 0</div>
                    </div>
                    <div class="card">
                        <h4>Available for Investment</h4>
                        <div class="value" id="availableInvestment">Rp 0</div>
                    </div>
                </div>

                <div class="chart-container">
                    <h3>Grafik Riwayat Pengeluaran Bulanan</h3>
                    <canvas id="expenseHistoryChart"></canvas>
                </div>
            </div>
        </div>
        
        <div id="investments" class="tab-content">
            <div class="section">
                <h3><span class="icon">📈</span>Investment Portfolio</h3>
                <div class="table-responsive">
                    <table id="investmentTable">
                        <thead>
                            <tr>
                                <th>Asset Type</th>
                                <th>Platform</th>
                                <th>Amount Invested (Rp)</th>
                                <th>Current Value (Rp)</th>
                                <th>Return (%)</th>
                                <th>Target Allocation (%)</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Saham</td>
                                <td><input type="text" id="sahamPlatform" placeholder="Ajaib/Stockbit"></td>
                                <td><input type="number" id="sahamInvested" placeholder="0"></td>
                                <td><input type="number" id="sahamValue" placeholder="0"></td>
                                <td id="sahamReturn">0%</td>
                                <td><span id="sahamTargetAllocation">60%</span></td>
                                <td><button class="btn" onclick="updateInvestment('saham')">Update</button></td>
                            </tr>
                            <tr>
                                <td>Emas</td>
                                <td><input type="text" id="emasPlatform" placeholder="Pegadaian/EmasDigi"></td>
                                <td><input type="number" id="emasInvested" placeholder="0"></td>
                                <td><input type="number" id="emasValue" placeholder="0"></td>
                                <td id="emasReturn">0%</td>
                                <td><span id="emasTargetAllocation">10%</span></td>
                                <td><button class="btn" onclick="updateInvestment('emas')">Update</button></td>
                            </tr>
                            <tr>
                                <td>Other Investment</td>
                                <td><input type="text" id="otherInvestmentPlatform" placeholder="P2P/Crypto/etc."></td>
                                <td><input type="number" id="otherInvestmentInvested" placeholder="0"></td>
                                <td><input type="number" id="otherInvestmentValue" placeholder="0"></td>
                                <td id="otherInvestmentReturn">0%</td>
                                <td><span id="otherInvestmentTargetAllocation">20%</span></td>
                                <td><button class="btn" onclick="updateInvestment('otherInvestment')">Update</button></td>
                            </tr>
                            <tr>
                                <td>Emergency Fund</td>
                                <td><input type="text" id="emergencyPlatform" placeholder="Bank/Money Market"></td>
                                <td><input type="number" id="emergencyInvested" placeholder="0"></td>
                                <td><input type="number" id="emergencyValue" placeholder="0"></td>
                                <td id="emergencyReturn">0%</td>
                                <td><span id="emergencyTargetAllocation">10%</span></td>
                                <td><button class="btn" onclick="updateInvestment('emergency')">Update</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="note success">
                    <strong>💡 Catatan Alokasi:</strong> Persentase alokasi di atas adalah contoh umum dan BUKAN nasihat keuangan. Sesuaikan dengan profil risiko dan tujuan finansial Anda. Selalu konsultasikan dengan perencana keuangan profesional.
                </div>

                <div class="summary-cards">
                    <div class="card">
                        <h4>Total Invested</h4>
                        <div class="value" id="totalInvested">Rp 0</div>
                    </div>
                    <div class="card">
                        <h4>Portfolio Value</h4>
                        <div class="value" id="portfolioValue">Rp 0</div>
                    </div>
                    <div class="card">
                        <h4>Total Return</h4>
                        <div class="value" id="totalReturn">0%</div>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="learning" class="tab-content">
            <div class="section">
                <h3><span class="icon">🎓</span>Skill Development Tracker</h3>
                <div class="table-responsive">
                    <table id="learningTable">
                        <thead>
                            <tr>
                                <th>Skill</th>
                                <th>Current Level</th>
                                <th>Target Level</th>
                                <th>Hours This Week</th>
                                <th>Total Hours</th>
                                <th>Resources</th>
                                <th>Next Milestone</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><input type="text" id="newSkillName" placeholder="Nama Skill"></td>
                                <td>
                                    <select id="newSkillLevel">
                                        <option>Beginner</option>
                                        <option>Intermediate</option>
                                        <option>Advanced</option>
                                        <option>Expert</option>
                                    </select>
                                </td>
                                <td><input type="text" id="newSkillTargetLevel" placeholder="Target Level"></td>
                                <td><input type="number" id="newSkillHours" placeholder="0"></td>
                                <td id="newSkillTotal">0</td>
                                <td><input type="text" id="newSkillResources" placeholder="Sumber Belajar"></td>
                                <td><input type="text" id="newSkillMilestone" placeholder="Milestone Berikutnya"></td>
                                <td><button class="btn" onclick="addSkill()">Add Skill</button></td>
                            </tr>
                            </tbody>
                    </table>
                </div>
            </div>
        </div>

        <div id="assets" class="tab-content">
            <div class="section">
                <h3><span class="icon">🏠</span>My Assets</h3>
                <div class="table-responsive">
                    <table id="assetsTable">
                        <thead>
                            <tr>
                                <th>Asset Name</th>
                                <th>Type</th>
                                <th>Current Value (Rp)</th>
                                <th>Acquisition Date</th>
                                <th>Notes</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><input type="text" id="assetName" placeholder="e.g., Rumah Utama"></td>
                                <td>
                                    <select id="assetType">
                                        <option>Real Estate</option>
                                        <option>Vehicle</option>
                                        <option>Collectibles</option>
                                        <option>Other</option>
                                    </select>
                                </td>
                                <td><input type="number" id="assetValue" placeholder="0"></td>
                                <td><input type="date" id="assetAcquisitionDate"></td>
                                <td><input type="text" id="assetNotes" placeholder="Catatan"></td>
                                <td><button class="btn" onclick="addAsset()">Add Asset</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <div class="summary-cards" id="assetSummaryCards">
                    </div>
            </div>
        </div>
        
        <div id="goals" class="tab-content">
            <div class="section">
                <h3><span class="icon">🎯</span>6-Year Wealth Goals</h3>
                <div class="table-responsive">
                    <table id="goalsTable">
                        <thead>
                            <tr>
                                <th>Year</th>
                                <th>Age</th>
                                <th>Income Target/Month</th>
                                <th>Net Worth Target</th>
                                <th>Current Net Worth</th>
                                <th>Progress</th>
                                <th>Key Milestones</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>1</td>
                                <td>20</td>
                                <td><input type="text" id="year1IncomeTarget" value="Rp 15M" readonly></td>
                                <td><input type="text" id="year1NetWorthTarget" value="Rp 40M" readonly></td>
                                <td><input type="number" id="year1Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year1Progress"></div></div></td>
                                <td>First clients, basic skills</td>
                                <td id="year1Status">In Progress</td>
                            </tr>
                            <tr>
                                <td>2</td>
                                <td>21</td>
                                <td><input type="text" id="year2IncomeTarget" value="Rp 25M" readonly></td>
                                <td><input type="text" id="year2NetWorthTarget" value="Rp 150M" readonly></td>
                                <td><input type="number" id="year2Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year2Progress"></div></div></td>
                                <td>Scale services, investments</td>
                                <td id="year2Status">Planned</td>
                            </tr>
                            <tr>
                                <td>3</td>
                                <td>22</td>
                                <td><input type="text" id="year3IncomeTarget" value="Rp 40M" readonly></td>
                                <td><input type="text" id="year3NetWorthTarget" value="Rp 400M" readonly></td>
                                <td><input type="number" id="year3Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year3Progress"></div></div></td>
                                <td>Business expansion</td>
                                <td id="year3Status">Planned</td>
                            </tr>
                            <tr>
                                <td>4</td>
                                <td>23</td>
                                <td><input type="text" id="year4IncomeTarget" value="Rp 60M" readonly></td>
                                <td><input type="text" id="year4NetWorthTarget" value="Rp 650M" readonly></td>
                                <td><input type="number" id="year4Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year4Progress"></div></div></td>
                                <td>Real estate, SaaS launch</td>
                                <td id="year4Status">Planned</td>
                            </tr>
                            <tr>
                                <td>5</td>
                                <td>24</td>
                                <td><input type="text" id="year5IncomeTarget" value="Rp 80M" readonly></td>
                                <td><input type="text" id="year5NetWorthTarget" value="Rp 900M" readonly></td>
                                <td><input type="number" id="year5Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year5Progress"></div></div></td>
                                <td>Multiple income streams</td>
                                <td id="year5Status">Planned</td>
                            </tr>
                            <tr>
                                <td>6</td>
                                <td>25</td>
                                <td><input type="text" id="year6IncomeTarget" value="Rp 100M" readonly></td>
                                <td><input type="text" id="year6NetWorthTarget" value="Rp 1.16B" readonly></td>
                                <td><input type="number" id="year6Current" placeholder="0"></td>
                                <td><div class="progress-bar"><div class="progress-fill" id="year6Progress"></div></div></td>
                                <td>🎉 GOAL ACHIEVED!</td>
                                <td id="year6Status">Planned</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <button class="btn btn-success" onclick="updateAllGoals()">Update All Progress</button>
                <button class="btn" onclick="exportData()">Export Data</button>
            </div>
        </div>
    </div>

    <script>
        // Global variable to store last month's expenses for snapshot if a new month starts
        let previousMonthFinalExpenses = null;

        // Inisialisasi penyimpanan data dari localStorage atau nilai default
        let data = {
            income: JSON.parse(localStorage.getItem('income')) || [],
            expenses: JSON.parse(localStorage.getItem('expenses')) || {
                living: { budget: 0, actual: 0 },
                tools: { budget: 0, actual: 0 },
                learning: { budget: 0, actual: 0 },
                marketing: { budget: 0, actual: 0 },
                lastUpdatedMonth: getCurrentMonthYear() // Initialize with current month
            },
            // Updated investments structure
            investments: JSON.parse(localStorage.getItem('investments')) || {
                saham: { invested: 0, value: 0, platform: '' },
                emas: { invested: 0, value: 0, platform: '' },
                otherInvestment: { invested: 0, value: 0, platform: '' },
                emergency: { invested: 0, value: 0, platform: '' } // Emergency fund as part of investments
            },
            expenseHistory: JSON.parse(localStorage.getItem('expenseHistory')) || [], // New: for monthly expenses history
            // Updated skills structure to be an array for dynamic addition
            skills: JSON.parse(localStorage.getItem('skills')) || [
                { id: 'html', name: 'HTML/CSS', level: 'Beginner', weekHours: 0, totalHours: 0, milestone: 'Build responsive website', targetLevel: 'Advanced', resources: 'freeCodeCamp, MDN' },
                { id: 'js', name: 'JavaScript', level: 'Beginner', weekHours: 0, totalHours: 0, milestone: 'Build interactive web app', targetLevel: 'Advanced', resources: 'JavaScript.info, freeCodeCamp' },
                { id: 'react', name: 'React', level: 'Beginner', weekHours: 0, totalHours: 0, milestone: 'Build full React app', targetLevel: 'Intermediate', resources: 'React Docs, Scrimba' },
                { id: 'marketingSkill', name: 'Digital Marketing', level: 'Beginner', weekHours: 0, totalHours: 0, milestone: 'Run profitable ad campaign', targetLevel: 'Advanced', resources: 'Google Digital Marketing, Neil Patel' }
            ],
            goals: JSON.parse(localStorage.getItem('goals')) || {
                year1: { currentNetWorth: 0, status: 'In Progress' },
                year2: { currentNetWorth: 0, status: 'Planned' },
                year3: { currentNetWorth: 0, status: 'Planned' },
                year4: { currentNetWorth: 0, status: 'Planned' },
                year5: { currentNetWorth: 0, status: 'Planned' },
                year6: { currentNetWorth: 0, status: 'Planned' }
            },
            // New: Assets structure
            assets: JSON.parse(localStorage.getItem('assets')) || []
        };

        // Target kekayaan bersih keseluruhan
        const NET_WORTH_TARGET = 1160000000; // Rp 1.16 Miliar

        // Chart instances
        let monthlyIncomeChartInstance;
        let expenseHistoryChartInstance; // New chart instance for expenses

        // Fungsi helper untuk memformat mata uang
        function formatCurrency(amount) {
            return `Rp ${new Intl.NumberFormat('id-ID').format(amount)}`;
        }

        // New helper function to get current month-year string
        function getCurrentMonthYear() {
            const now = new Date();
            return `${now.getFullYear()}-${(now.getMonth() + 1).toString().padStart(2, '0')}`;
        }

        // Fungsi helper untuk parsing nilai target dari teks (misal: "Rp 40M", "Rp 1.16B")
        function parseTargetValue(text) {
            text = text.replace('Rp ', '').trim();
            if (text.endsWith('M')) {
                return parseFloat(text.replace('M', '')) * 1_000_000;
            } else if (text.endsWith('B')) {
                // Menangani kasus seperti "1.16B"
                return parseFloat(text.replace('B', '')) * 1_000_000_000;
            }
            // Hapus pemisah ribuan (titik) sebelum parsing angka
            return parseFloat(text.replace(/\./g, '')) || 0; 
        }

        // Fungsi untuk menampilkan pesan notifikasi kustom
        function showMessage(message, type = 'success') {
            const messageBox = document.getElementById('messageBox');
            const messageText = document.getElementById('messageText');
            messageText.textContent = message;
            messageBox.className = 'message-box'; // Reset kelas
            if (type === 'error') {
                messageBox.classList.add('error');
            } else if (type === 'info') { // New 'info' type
                messageBox.classList.add('success'); // Using success style for info
            }
            messageBox.style.display = 'flex';
            setTimeout(() => {
                messageBox.style.display = 'none';
            }, 3000); // Sembunyikan setelah 3 detik
        }

        // Fungsi untuk menyimpan data ke localStorage
        function saveData() {
            localStorage.setItem('income', JSON.stringify(data.income));
            localStorage.setItem('expenses', JSON.stringify(data.expenses));
            localStorage.setItem('investments', JSON.stringify(data.investments));
            localStorage.setItem('expenseHistory', JSON.stringify(data.expenseHistory)); // Save new data
            localStorage.setItem('skills', JSON.stringify(data.skills));
            localStorage.setItem('goals', JSON.stringify(data.goals));
            localStorage.setItem('assets', JSON.stringify(data.assets)); // Save new data
        }

        // Logika pengalihan tab
        function showTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            document.getElementById(tabId).classList.add('active');
            document.querySelector(`.nav-tab[onclick="showTab('${tabId}')"]`).classList.add('active');
            updateDashboard(); // Perbarui dashboard setiap kali tab dialihkan
            loadDataIntoForms(); // Muat data saat tab dialihkan

            // Render charts specific to the active tab
            if (tabId === 'income') {
                renderMonthlyIncomeChart();
            } else if (tabId === 'expenses') {
                renderExpenseHistoryChart(); // Render expenses history chart
            }
            // Removed investment and learning charts as per request
        }

        // --- Fungsi Pelacak Pemasukan ---
        function calculateIncomeRate() {
            const amount = parseFloat(document.getElementById('incomeAmount').value) || 0;
            const hours = parseFloat(document.getElementById('incomeHours').value) || 0;
            const rate = hours > 0 ? (amount / hours).toFixed(2) : 0;
            document.getElementById('incomeRate').value = rate;
        }

        // Tambahkan event listener untuk perhitungan rate otomatis
        document.getElementById('incomeAmount').addEventListener('input', calculateIncomeRate);
        document.getElementById('incomeHours').addEventListener('input', calculateIncomeRate);

        function addIncome() {
            const date = document.getElementById('incomeDate').value;
            const source = document.getElementById('incomeSource').value; // Now a text input
            const type = document.getElementById('incomeType').value;
            const client = document.getElementById('clientName').value;
            const amount = parseFloat(document.getElementById('incomeAmount').value) || 0;
            const hours = parseFloat(document.getElementById('incomeHours').value) || 0;
            const rate = parseFloat(document.getElementById('incomeRate').value) || 0;
            const status = document.getElementById('incomeStatus').value;

            if (!date || !source || amount <= 0) {
                showMessage('Harap isi Tanggal, Sumber, dan Jumlah Pemasukan (harus lebih dari 0).', 'error');
                return;
            }

            data.income.push({
                date,
                source,
                type,
                client,
                amount,
                hours,
                rate,
                status
            });
            saveData();
            renderIncomeTable();
            updateDashboard();
            clearIncomeForm();
            renderMonthlyIncomeChart(); // Update chart
            showMessage('Pemasukan berhasil ditambahkan!', 'success');
        }

        function renderIncomeTable() {
            const tableBody = document.querySelector('#incomeTable tbody');
            // Hapus baris yang ada kecuali baris input
            const rows = tableBody.querySelectorAll('tr');
            for (let i = 1; i < rows.length; i++) { // Mulai dari 1 untuk mempertahankan baris input
                rows[i].remove();
            }

            data.income.forEach((item, index) => {
                const newRow = tableBody.insertRow(-1); // Sisipkan di akhir
                newRow.innerHTML = `
                    <td>${item.date}</td>
                    <td>${item.source}</td>
                    <td>${item.type}</td>
                    <td>${item.client}</td>
                    <td>${formatCurrency(item.amount)}</td>
                    <td>${item.hours}</td>
                    <td>${formatCurrency(item.rate)}</td>
                    <td>${item.status}</td>
                    <td><button class="btn btn-danger" onclick="deleteIncome(${index})">Delete</button></td>
                `;
            });
        }

        function deleteIncome(index) {
            data.income.splice(index, 1);
            saveData();
            renderIncomeTable();
            updateDashboard();
            renderMonthlyIncomeChart(); // Update chart
            showMessage('Pemasukan berhasil dihapus.', 'success');
        }

        function clearIncomeForm() {
            document.getElementById('incomeDate').value = '';
            document.getElementById('incomeSource').value = ''; // Clear text input
            document.getElementById('incomeType').value = 'Project';
            document.getElementById('clientName').value = '';
            document.getElementById('incomeAmount').value = '';
            document.getElementById('incomeHours').value = '';
            document.getElementById('incomeRate').value = '';
            document.getElementById('incomeStatus').value = 'Pending';
        }

        function renderMonthlyIncomeChart() {
            const ctx = document.getElementById('monthlyIncomeChart').getContext('2d');
            if (monthlyIncomeChartInstance) {
                monthlyIncomeChartInstance.destroy();
            }

            const monthlyData = {};
            data.income.filter(inc => inc.status === 'Paid').forEach(inc => {
                const monthYear = inc.date.substring(0, 7); //YYYY-MM
                if (!monthlyData[monthYear]) {
                    monthlyData[monthYear] = 0;
                }
                monthlyData[monthYear] += inc.amount;
            });

            const labels = Object.keys(monthlyData).sort();
            const monthlyAmounts = labels.map(month => monthlyData[month]);

            // Calculate cumulative income
            let cumulativeSum = 0;
            const cumulativeAmounts = monthlyAmounts.map(amount => {
                cumulativeSum += amount;
                return cumulativeSum;
            });

            monthlyIncomeChartInstance = new Chart(ctx, {
                type: 'bar', // Use bar chart for monthly income
                data: {
                    labels: labels,
                    datasets: [
                        {
                            label: 'Pendapatan Bulanan (Rp)',
                            data: monthlyAmounts,
                            backgroundColor: 'rgba(50, 130, 184, 0.8)', // Blue
                            borderColor: 'rgba(50, 130, 184, 1)',
                            borderWidth: 1,
                            yAxisID: 'y'
                        },
                        {
                            label: 'Pendapatan Kumulatif (Rp)',
                            data: cumulativeAmounts,
                            type: 'line', // Use line for cumulative
                            borderColor: 'rgba(40, 167, 69, 1)', // Green
                            backgroundColor: 'rgba(40, 167, 69, 0.2)',
                            fill: true,
                            tension: 0.3,
                            yAxisID: 'y1'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            ticks: { color: '#e0e0e0' },
                            grid: { color: '#3a4768' }
                        },
                        y: {
                            beginAtZero: true,
                            ticks: {
                                color: '#e0e0e0',
                                callback: function(value) {
                                    return formatCurrency(value);
                                }
                            },
                            grid: { color: '#3a4768' }
                        },
                        y1: {
                            type: 'linear',
                            display: true,
                            position: 'right',
                            beginAtZero: true,
                            ticks: {
                                color: '#e0e0e0',
                                callback: function(value) {
                                    return formatCurrency(value);
                                }
                            },
                            grid: { drawOnChartArea: false } // Only draw grid for y-axis
                        }
                    },
                    plugins: {
                        legend: {
                            labels: {
                                color: '#e0e0e0'
                            }
                        }
                    }
                }
            });
        }


        // --- Fungsi Pelacak Pengeluaran ---

        // Function to update expense display and related calculations
        function updateExpenseDisplay(category) {
            const budget = parseFloat(document.getElementById(`${category}Budget`).value) || 0;
            const actual = parseFloat(data.expenses[category].actual) || 0; // Use data.expenses.actual

            const diffCell = document.getElementById(`${category}Diff`);
            const percentCell = document.getElementById(`${category}Percent`);

            const difference = budget - actual;
            diffCell.textContent = formatCurrency(difference);
            diffCell.style.color = difference >= 0 ? '#28a745' : '#dc3545';

            const totalMonthlyIncome = data.income.filter(inc => inc.status === 'Paid')
                                    .reduce((sum, inc) => sum + inc.amount, 0);
            const percentOfIncome = totalMonthlyIncome > 0 ? ((actual / totalMonthlyIncome) * 100).toFixed(2) : 0;
            percentCell.textContent = `${percentOfIncome}%`;
        }

        // New function to record new expense
        function recordNewExpense(category) {
            const newExpenseInput = document.getElementById(`new${category.charAt(0).toUpperCase() + category.slice(1)}Expense`);
            const newExpenseAmount = parseFloat(newExpenseInput.value) || 0;

            if (newExpenseAmount <= 0) {
                showMessage('Jumlah pengeluaran baru harus lebih dari 0.', 'error');
                return;
            }

            // Add new expense to current actual total
            data.expenses[category].actual += newExpenseAmount;
            
            // Update the readonly actual field
            document.getElementById(`${category}Actual`).value = data.expenses[category].actual;

            // Update display and summary
            updateExpenseDisplay(category);
            updateExpensesSummary();

            // Clear the new expense input field
            newExpenseInput.value = '';

            // Update the expense history snapshot for the current month
            updateExpenseHistorySnapshot();
            saveData();
            updateDashboard();
            showMessage(`Pengeluaran baru untuk ${category} berhasil ditambahkan!`, 'success');
        }

        function updateExpensesSummary() {
            let totalActualExpenses = 0;
            for (const category in data.expenses) {
                if (category !== 'lastUpdatedMonth') { // Exclude lastUpdatedMonth property
                    totalActualExpenses += data.expenses[category].actual;
                }
            }
            document.getElementById('totalExpenses').textContent = formatCurrency(totalActualExpenses);

            const totalPaidIncome = data.income.filter(inc => inc.status === 'Paid')
                                    .reduce((sum, inc) => sum + inc.amount, 0);
            const availableForInvestment = totalPaidIncome - totalActualExpenses;
            document.getElementById('availableInvestment').textContent = formatCurrency(availableForInvestment);
        }

        // Modified loadExpensesIntoForm to populate readonly fields and handle new expense inputs
        function loadExpensesIntoForm() {
            for (const category in data.expenses) {
                if (category !== 'lastUpdatedMonth') { // Exclude lastUpdatedMonth property
                    document.getElementById(`${category}Budget`).value = data.expenses[category].budget;
                    document.getElementById(`${category}Actual`).value = data.expenses[category].actual; // Populate readonly actual
                    document.getElementById(`new${category.charAt(0).toUpperCase() + category.slice(1)}Expense`).value = ''; // Clear new expense input

                    updateExpenseDisplay(category); // Update diff and percent
                }
            }
            updateExpensesSummary();
            renderExpenseHistoryChart(); // Render chart on load
        }

        // Function to update the expense history snapshot for the current month
        function updateExpenseHistorySnapshot() {
            const currentMonthYear = getCurrentMonthYear();
            const currentActualExpenses = {};
            for (const category in data.expenses) {
                if (category !== 'lastUpdatedMonth') {
                    currentActualExpenses[category] = data.expenses[category].actual;
                }
            }

            const existingSnapshotIndex = data.expenseHistory.findIndex(snapshot => snapshot.monthYear === currentMonthYear);

            if (existingSnapshotIndex !== -1) {
                // Update existing snapshot
                data.expenseHistory[existingSnapshotIndex].expenses = currentActualExpenses;
            } else {
                // Add new snapshot
                data.expenseHistory.push({
                    monthYear: currentMonthYear,
                    expenses: currentActualExpenses
                });
                data.expenseHistory.sort((a, b) => a.monthYear.localeCompare(b.monthYear)); // Keep sorted
            }
        }

        // Function to check month and reset expenses
        function checkMonthAndResetExpenses() {
            const currentMonthYear = getCurrentMonthYear();
            let lastRecordedMonth = data.expenses.lastUpdatedMonth;

            // If lastUpdatedMonth is not defined or is older than currentMonthYear
            if (!lastRecordedMonth || lastRecordedMonth < currentMonthYear) {
                // This is a new month. Store previous month's finalized data if it exists.
                if (lastRecordedMonth) { // Only log if it's not the very first load
                    const previousMonthSnapshot = {
                        monthYear: lastRecordedMonth,
                        expenses: {}
                    };
                    for (const category in data.expenses) {
                        if (category !== 'lastUpdatedMonth') {
                            previousMonthSnapshot.expenses[category] = data.expenses[category].actual;
                        }
                    }
                    // Add or update the previous month's snapshot in history
                    const existingSnapshotIndex = data.expenseHistory.findIndex(s => s.monthYear === previousMonthSnapshot.monthYear);
                    if (existingSnapshotIndex !== -1) {
                        data.expenseHistory[existingSnapshotIndex] = previousMonthSnapshot;
                    } else {
                        data.expenseHistory.push(previousMonthSnapshot);
                    }
                }

                // Reset current month's actual expenses to zero
                for (const category in data.expenses) {
                    if (category !== 'lastUpdatedMonth') {
                        data.expenses[category].actual = 0;
                    }
                }
                data.expenses.lastUpdatedMonth = currentMonthYear; // Update the last recorded month
                saveData(); // Save the state after reset and history update
                showMessage(`Bulan baru! Pengeluaran bulan ini telah diatur ulang.`, 'info'); // 'info' type for message
                // Re-render expense table and chart to reflect the reset
                loadExpensesIntoForm();
                renderExpenseHistoryChart();
            }
        }

        // New function to render expenses history chart
        function renderExpenseHistoryChart() {
            const ctx = document.getElementById('expenseHistoryChart').getContext('2d');
            if (expenseHistoryChartInstance) {
                expenseHistoryChartInstance.destroy();
            }

            const labels = data.expenseHistory.map(snapshot => snapshot.monthYear).sort();
            const categories = ['living', 'tools', 'learning', 'marketing']; // Define categories explicitly for consistent order

            const datasets = categories.map(category => {
                const colors = {
                    'living': { bg: 'rgba(255, 99, 132, 0.8)', border: 'rgba(255, 99, 132, 1)' }, // Red
                    'tools': { bg: 'rgba(54, 162, 235, 0.8)', border: 'rgba(54, 162, 235, 1)' },   // Blue
                    'learning': { bg: 'rgba(255, 206, 86, 0.8)', border: 'rgba(255, 206, 86, 1)' }, // Yellow
                    'marketing': { bg: 'rgba(75, 192, 192, 0.8)', border: 'rgba(75, 192, 192, 1)' } // Green
                };
                const color = colors[category] || { bg: 'rgba(150, 150, 150, 0.8)', border: 'rgba(150, 150, 150, 1)' }; // Default grey

                return {
                    label: category.charAt(0).toUpperCase() + category.slice(1),
                    data: labels.map(monthYear => {
                        const snapshot = data.expenseHistory.find(s => s.monthYear === monthYear);
                        return snapshot && snapshot.expenses ? snapshot.expenses[category] || 0 : 0;
                    }),
                    backgroundColor: color.bg,
                    borderColor: color.border,
                    borderWidth: 1
                };
            });

            expenseHistoryChartInstance = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: labels,
                    datasets: datasets
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            stacked: true, // Stack bars
                            ticks: { color: '#e0e0e0' },
                            grid: { color: '#3a4768' }
                        },
                        y: {
                            stacked: true, // Stack bars
                            beginAtZero: true,
                            ticks: {
                                color: '#e0e0e0',
                                callback: function(value) {
                                    return formatCurrency(value);
                                },
                                maxTicksLimit: 7 // Limit the number of ticks on the y-axis
                            },
                            grid: { color: '#3a4768' }
                        }
                    },
                    plugins: {
                        legend: {
                            labels: {
                                color: '#e0e0e0'
                            }
                        }
                    }
                }
            });
        }


        // --- Fungsi Pelacak Investasi ---
        // Pindahkan definisi updateInvestmentSummary ke atas agar dapat diakses
        function updateInvestmentSummary() {
            let totalInvested = 0;
            let totalPortfolioValue = 0;
            for (const assetType in data.investments) {
                totalInvested += data.investments[assetType].invested;
                totalPortfolioValue += data.investments[assetType].value;
            }
            document.getElementById('totalInvested').textContent = formatCurrency(totalInvested);
            document.getElementById('portfolioValue').textContent = formatCurrency(totalPortfolioValue);

            let overallReturn = 0;
            if (totalInvested > 0) {
                overallReturn = (((totalPortfolioValue - totalInvested) / totalInvested) * 100).toFixed(2);
            }
            document.getElementById('totalReturn').textContent = `${overallReturn}%`;
            document.getElementById('totalReturn').style.color = overallReturn >= 0 ? '#28a745' : '#dc3545';
        }

        function updateInvestment(assetType) {
            const platformInput = document.getElementById(`${assetType}Platform`);
            const investedInput = document.getElementById(`${assetType}Invested`);
            const valueInput = document.getElementById(`${assetType}Value`);
            const returnCell = document.getElementById(`${assetType}Return`);

            const platform = platformInput.value;
            const invested = parseFloat(investedInput.value) || 0;
            const value = parseFloat(valueInput.value) || 0;

            data.investments[assetType].platform = platform;
            data.investments[assetType].invested = invested;
            data.investments[assetType].value = value;

            let investmentReturn = 0;
            if (invested > 0) {
                investmentReturn = (((value - invested) / invested) * 100).toFixed(2);
            }
            returnCell.textContent = `${investmentReturn}%`;
            returnCell.style.color = investmentReturn >= 0 ? '#28a745' : '#dc3545'; // Hijau jika positif, merah jika negatif

            saveData();
            updateDashboard();
            updateInvestmentSummary();
            showMessage(`Investasi ${assetType} berhasil diperbarui.`, 'success');
        }

        function loadInvestmentsIntoForm() {
            for (const assetType in data.investments) {
                // Periksa apakah elemen ada sebelum mencoba mengatur nilainya
                const platformElement = document.getElementById(`${assetType}Platform`);
                if (platformElement) platformElement.value = data.investments[assetType].platform;
                
                const investedElement = document.getElementById(`${assetType}Invested`);
                if (investedElement) investedElement.value = data.investments[assetType].invested;
                
                const valueElement = document.getElementById(`${assetType}Value`);
                if (valueElement) valueElement.value = data.investments[assetType].value;
                

                // Hitung ulang dan tampilkan pengembalian
                const invested = data.investments[assetType].invested;
                const value = data.investments[assetType].value;
                let investmentReturn = 0;
                if (invested > 0) {
                    investmentReturn = (((value - invested) / invested) * 100).toFixed(2);
                }
                const returnCell = document.getElementById(`${assetType}Return`);
                if (returnCell) { // Periksa apakah elemen ada
                    returnCell.textContent = `${investmentReturn}%`;
                    returnCell.style.color = investmentReturn >= 0 ? '#28a745' : '#dc3545';
                }
            }
            updateInvestmentSummary();
        }


        // --- Fungsi Pelacak Pembelajaran ---
        // New function to add a skill dynamically
        function addSkill() {
            const skillName = document.getElementById('newSkillName').value.trim();
            const skillLevel = document.getElementById('newSkillLevel').value;
            const skillTargetLevel = document.getElementById('newSkillTargetLevel').value.trim();
            const skillHours = parseFloat(document.getElementById('newSkillHours').value) || 0;
            const skillResources = document.getElementById('newSkillResources').value.trim();
            const skillMilestone = document.getElementById('newSkillMilestone').value.trim();

            if (!skillName) {
                showMessage('Nama Skill tidak boleh kosong.', 'error');
                return;
            }

            // Generate a simple ID for the new skill (ensure uniqueness if possible, or handle duplicates)
            const newSkillId = skillName.toLowerCase().replace(/\s/g, '') + Date.now(); // Add timestamp for uniqueness

            data.skills.push({
                id: newSkillId,
                name: skillName,
                level: skillLevel,
                targetLevel: skillTargetLevel,
                weekHours: skillHours,
                totalHours: skillHours, // Initial total hours
                resources: skillResources,
                milestone: skillMilestone
            });
            saveData();
            renderLearningTable();
            clearNewSkillForm();
            showMessage(`Skill '${skillName}' berhasil ditambahkan!`, 'success');
        }

        // Modified updateSkill to work with array of skills
        function updateSkill(skillId) {
            const skillIndex = data.skills.findIndex(s => s.id === skillId);
            if (skillIndex === -1) {
                showMessage('Skill tidak ditemukan.', 'error');
                return;
            }

            const skill = data.skills[skillIndex];
            
            // Ensure elements exist before accessing their values
            const levelSelect = document.getElementById(`${skillId}Level`);
            const hoursInput = document.getElementById(`${skillId}Hours`);
            const milestoneInput = document.getElementById(`${skillId}Milestone`);
            const targetLevelInput = document.getElementById(`${skillId}TargetLevel`);
            const resourcesInput = document.getElementById(`${skillId}Resources`);
            const totalHoursCell = document.getElementById(`${skillId}Total`);


            if (levelSelect) skill.level = levelSelect.value;
            const hoursThisWeek = parseFloat(hoursInput ? hoursInput.value : 0) || 0;
            skill.weekHours = hoursThisWeek;
            skill.totalHours += hoursThisWeek; // Accumulate total hours
            if (milestoneInput) skill.milestone = milestoneInput.value;
            if (targetLevelInput) skill.targetLevel = targetLevelInput.value;
            if (resourcesInput) skill.resources = resourcesInput.value;

            if (totalHoursCell) totalHoursCell.textContent = skill.totalHours;

            saveData();
            if (hoursInput) hoursInput.value = ''; // Clear hours this week input after update
            showMessage(`Skill '${skill.name}' berhasil diperbarui.`, 'success');
        }

        // New function to delete a skill
        function deleteSkill(skillId) {
            data.skills = data.skills.filter(s => s.id !== skillId);
            saveData();
            renderLearningTable();
            showMessage('Skill berhasil dihapus.', 'success');
        }

        // Modified loadSkillsIntoForm to render the table dynamically
        function renderLearningTable() {
            const tableBody = document.querySelector('#learningTable tbody');
            // Clear existing rows except the input row (which is the first child)
            const existingRows = tableBody.querySelectorAll('tr:not(:first-child)');
            existingRows.forEach(row => row.remove());

            data.skills.forEach(skill => {
                const newRow = tableBody.insertRow(-1);
                newRow.innerHTML = `
                    <td>${skill.name}</td>
                    <td>
                        <select id="${skill.id}Level" onchange="updateSkill('${skill.id}')">
                            <option value="Beginner" ${skill.level === 'Beginner' ? 'selected' : ''}>Beginner</option>
                            <option value="Intermediate" ${skill.level === 'Intermediate' ? 'selected' : ''}>Intermediate</option>
                            <option value="Advanced" ${skill.level === 'Advanced' ? 'selected' : ''}>Advanced</option>
                            <option value="Expert" ${skill.level === 'Expert' ? 'selected' : ''}>Expert</option>
                        </select>
                    </td>
                    <td><input type="text" id="${skill.id}TargetLevel" value="${skill.targetLevel}" onchange="updateSkill('${skill.id}')"></td>
                    <td><input type="number" id="${skill.id}Hours" placeholder="0"></td>
                    <td id="${skill.id}Total">${skill.totalHours}</td>
                    <td><input type="text" id="${skill.id}Resources" value="${skill.resources}" onchange="updateSkill('${skill.id}')"></td>
                    <td><input type="text" id="${skill.id}Milestone" value="${skill.milestone}" onchange="updateSkill('${skill.id}')"></td>
                    <td>
                        <button class="btn btn-success" onclick="updateSkill('${skill.id}')">Update</button>
                        <button class="btn btn-danger" onclick="deleteSkill('${skill.id}')">Delete</button>
                    </td>
                `;
            });
        }

        function clearNewSkillForm() {
            document.getElementById('newSkillName').value = '';
            document.getElementById('newSkillLevel').value = 'Beginner';
            document.getElementById('newSkillTargetLevel').value = '';
            document.getElementById('newSkillHours').value = '';
            document.getElementById('newSkillResources').value = '';
            document.getElementById('newSkillMilestone').value = '';
        }


        // --- Fungsi Pelacak Tujuan ---
        function updateAllGoals() {
            let totalNetWorth = 0;
            // Hitung total kekayaan bersih dari nilai portofolio investasi
            for (const assetType in data.investments) {
                totalNetWorth += data.investments[assetType].value;
            }
            
            // Tambahkan sisa uang tunai (pemasukan yang dibayar - pengeluaran aktual) sebagai bagian dari kekayaan bersih
            const totalPaidIncome = data.income.filter(inc => inc.status === 'Paid').reduce((sum, inc) => sum + inc.amount, 0);
            let totalActualExpenses = 0;
            for (const category in data.expenses) {
                if (category !== 'lastUpdatedMonth') {
                    totalActualExpenses += data.expenses[category].actual;
                }
            }
            totalNetWorth += (totalPaidIncome - totalActualExpenses); // Tambahkan sisa uang tunai ke kekayaan bersih

            // Tambahkan nilai aset fisik ke kekayaan bersih
            totalNetWorth += data.assets.reduce((sum, asset) => sum + asset.value, 0);


            // Perbarui kekayaan bersih saat ini untuk setiap tujuan tahunan
            for (let i = 1; i <= 6; i++) {
                const yearId = `year${i}`;
                const currentNetWorthInput = document.getElementById(`${yearId}Current`);
                // Get target from the input field value, not textContent
                const netWorthTargetText = document.getElementById(`${yearId}NetWorthTarget`).value;
                const netWorthTarget = parseTargetValue(netWorthTargetText);
                
                // Perbarui bidang input dengan totalNetWorth yang dihitung
                if (currentNetWorthInput) currentNetWorthInput.value = totalNetWorth;
                data.goals[yearId].currentNetWorth = totalNetWorth;

                const progressFill = document.getElementById(`${yearId}Progress`);
                let progress = (totalNetWorth / netWorthTarget) * 100;
                if (progress > 100) progress = 100;
                if (progressFill) progressFill.style.width = `${progress}%`;

                const statusCell = document.getElementById(`${yearId}Status`);
                if (statusCell) { // Periksa apakah elemen ada
                    if (totalNetWorth >= netWorthTarget) {
                        statusCell.textContent = 'Achieved';
                        statusCell.style.color = '#28a745';
                        data.goals[yearId].status = 'Achieved';
                    } else {
                        // Jika belum mencapai target, statusnya "In Progress" jika sudah ada progres, atau "Planned"
                        if (data.goals[yearId].status === 'Planned' && progress > 0) {
                            statusCell.textContent = 'In Progress';
                            statusCell.style.color = '#3282b8';
                            data.goals[yearId].status = 'In Progress';
                        } else if (data.goals[yearId].status === 'In Progress') {
                            statusCell.textContent = 'In Progress';
                            statusCell.style.color = '#3282b8';
                        } else { // Jika masih 0% progres
                            statusCell.textContent = 'Planned';
                            statusCell.style.color = '#a0a0a0';
                        }
                    }
                }
            }
            saveData();
            updateDashboard(); // Pastikan dashboard mencerminkan kekayaan bersih terbaru
            showMessage('Progres tujuan berhasil diperbarui!', 'success');
        }
        
        function loadGoalsIntoForm() {
            for (let i = 1; i <= 6; i++) {
                const yearId = `year${i}`;
                const currentNetWorthInput = document.getElementById(`${yearId}Current`);
                if (currentNetWorthInput) currentNetWorthInput.value = data.goals[yearId].currentNetWorth;
                
                // Get target from the input field value, not textContent
                const netWorthTargetText = document.getElementById(`${yearId}NetWorthTarget`).value;
                const netWorthTarget = parseTargetValue(netWorthTargetText);

                const progressFill = document.getElementById(`${yearId}Progress`);
                let progress = (data.goals[yearId].currentNetWorth / netWorthTarget) * 100;
                if (progress > 100) progress = 100;
                if (progressFill) progressFill.style.width = `${progress}%`;
                
                const statusCell = document.getElementById(`${yearId}Status`);
                if (statusCell) { // Periksa apakah elemen ada
                    statusCell.textContent = data.goals[yearId].status;
            
                    statusCell.style.color = data.goals[yearId].status === 'Achieved' ? '#28a745' : (data.goals[yearId].status === 'In Progress' ? '#3282b8' : '#a0a0a0');
                }
            }
        }


        // --- New Assets Functions ---
        function addAsset() {
            const name = document.getElementById('assetName').value.trim();
            const type = document.getElementById('assetType').value;
            const value = parseFloat(document.getElementById('assetValue').value) || 0;
            const acquisitionDate = document.getElementById('assetAcquisitionDate').value;
            const notes = document.getElementById('assetNotes').value.trim();

            if (!name || value <= 0) {
                showMessage('Nama aset dan Nilai (harus lebih dari 0) harus diisi.', 'error');
                return;
            }

            data.assets.push({ name, type, value, acquisitionDate, notes });
            saveData();
            renderAssetsTable();
            renderAssetSummaryCards(); // Update summary cards
            updateDashboard();
            clearAssetForm();
            showMessage('Aset berhasil ditambahkan!', 'success');
        }

        function renderAssetsTable() {
            const tableBody = document.querySelector('#assetsTable tbody');
            // Clear existing rows except the input row
            const rows = tableBody.querySelectorAll('tr');
            for (let i = 1; i < rows.length; i++) { // Start from 1 to preserve input row
                rows[i].remove();
            }

            data.assets.forEach((asset, index) => {
                const newRow = tableBody.insertRow(-1);
                newRow.innerHTML = `
                    <td>${asset.name}</td>
                    <td>${asset.type}</td>
                    <td>${formatCurrency(asset.value)}</td>
                    <td>${asset.acquisitionDate}</td>
                    <td>${asset.notes}</td>
                    <td><button class="btn btn-danger" onclick="deleteAsset(${index})">Delete</button></td>
                `;
            });
        }

        function deleteAsset(index) {
            data.assets.splice(index, 1);
            saveData();
            renderAssetsTable();
            renderAssetSummaryCards(); // Update summary cards
            updateDashboard();
            showMessage('Aset berhasil dihapus.', 'success');
        }

        function clearAssetForm() {
            document.getElementById('assetName').value = '';
            document.getElementById('assetType').value = 'Real Estate';
            document.getElementById('assetValue').value = '';
            document.getElementById('assetAcquisitionDate').value = '';
            document.getElementById('assetNotes').value = '';
        }

        // New function to render asset summary cards
        function renderAssetSummaryCards() {
            const assetSummaryContainer = document.getElementById('assetSummaryCards');
            assetSummaryContainer.innerHTML = ''; // Clear existing cards

            const assetTotalsByType = {};
            data.assets.forEach(asset => {
                if (!assetTotalsByType[asset.type]) {
                    assetTotalsByType[asset.type] = 0;
                }
                assetTotalsByType[asset.type] += asset.value;
            });

            for (const type in assetTotalsByType) {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <h4>Total ${type} Value</h4>
                    <div class="value">${formatCurrency(assetTotalsByType[type])}</div>
                `;
                assetSummaryContainer.appendChild(card);
            }

            if (Object.keys(assetTotalsByType).length === 0) {
                assetSummaryContainer.innerHTML = '<p style="color: #a0a0a0; text-align: center;">Tidak ada aset yang tercatat.</p>';
            }
        }


        // --- Fungsi Pembaruan Dashboard ---
        function updateDashboard() {
            // Hitung Pemasukan Bulanan (jumlah pemasukan 'Paid')
            const monthlyIncome = data.income
                .filter(inc => inc.status === 'Paid')
                .reduce((sum, inc) => sum + inc.amount, 0);
            document.getElementById('monthlyIncome').textContent = formatCurrency(monthlyIncome);

            // Hitung Total Pengeluaran Aktual
            let totalActualExpenses = 0;
            for (const category in data.expenses) {
                if (category !== 'lastUpdatedMonth') {
                    totalActualExpenses += data.expenses[category].actual;
                }
            }

            // Hitung Kekayaan Bersih Saat Ini (Nilai Portofolio Investasi + Sisa Cash + Nilai Aset Fisik)
            let currentNetWorth = 0;
            for (const assetType in data.investments) {
                currentNetWorth += data.investments[assetType].value;
            }
            // Tambahkan uang tunai (perkiraan sederhana: pemasukan bulanan - pengeluaran bulanan)
            currentNetWorth += (monthlyIncome - totalActualExpenses);
            // Tambahkan nilai aset fisik
            currentNetWorth += data.assets.reduce((sum, asset) => sum + asset.value, 0);


            document.getElementById('totalNetWorth').textContent = formatCurrency(currentNetWorth);

            // Perbarui Bilah Progres Kekayaan Bersih
            const netWorthProgress = (currentNetWorth / NET_WORTH_TARGET) * 100;
            document.getElementById('netWorthProgress').style.width = `${Math.min(netWorthProgress, 100)}%`;

            // Hitung Tingkat Tabungan
            let savingsRate = 0;
            if (monthlyIncome > 0) {
                const totalSaved = monthlyIncome - totalActualExpenses;
                savingsRate = ((totalSaved / monthlyIncome) * 100).toFixed(2);
            }
            document.getElementById('savingsRate').textContent = `${savingsRate}%`;
            document.getElementById('savingsRate').style.color = savingsRate >= 50 ? '#28a745' : '#dc3545';


            // Hitung Pengembalian Investasi (Keseluruhan)
            let totalInvested = 0;
            let totalPortfolioValue = 0;
            for (const assetType in data.investments) {
                totalInvested += data.investments[assetType].invested;
                totalPortfolioValue += data.investments[assetType].value;
            }
            let overallInvestmentReturn = 0;
            if (totalInvested > 0) {
                overallInvestmentReturn = (((totalPortfolioValue - totalInvested) / totalInvested) * 100).toFixed(2);
            }
            document.getElementById('investmentReturns').textContent = `${overallInvestmentReturn}%`;
            document.getElementById('investmentReturns').style.color = overallInvestmentReturn >= 20 ? '#28a745' : '#dc3545';
        }

        // --- Muat Awal dan Persistensi Data ---
        function loadDataIntoForms() {
            renderIncomeTable();
            loadExpensesIntoForm();
            loadInvestmentsIntoForm();
            renderLearningTable(); // Render learning table
            renderAssetsTable(); // Render assets table
            renderAssetSummaryCards(); // Render asset summary cards
            loadGoalsIntoForm();
        }

        // Ekspor Data ke JSON
        function exportData() {
            const dataStr = JSON.stringify(data, null, 2);
            const blob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'wealth_tracker_data.json';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            showMessage('Data berhasil diekspor!', 'success');
        }

        // Saat halaman dimuat
        document.addEventListener('DOMContentLoaded', () => {
            checkMonthAndResetExpenses(); // Perform month check and reset on load
            loadDataIntoForms();
            updateDashboard();
        });

        // Pendaftaran Service Worker
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('/sw.js')
                    .then(registration => {
                        console.log('ServiceWorker registered: ', registration.scope);
                    })
                    .catch(error => {
                        console.log('ServiceWorker registration failed: ', error);
                    });
            });
        }

    </script>
</body>
</html>
