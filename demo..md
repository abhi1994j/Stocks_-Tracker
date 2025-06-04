 <!-- <header class="text-center bg-gray-800 text-white py-6"> 
      <h1 class="text-3xl font-bold">Stock Tracker Dashboard</h1>
    </header>

    <main class="p-6 max-w-5xl mx-auto">
      
      <section class="mb-6 text-center">
        <h2 class="text-xl font-semibold mb-2">Select Trending Stock</h2>
        <div
          class="flex flex-col sm:flex-row justify-center items-center gap-4"
        >
          <select
            id="stockDropdown"
            class="px-4 py-2 text-base w-72 border border-gray-300 rounded-md"
          >
            
          </select>
          <button
            id="loadStockButton"
            class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700"
          >
            Load Stock
          </button>
        </div>
      </section> 
      <section
        class="mb-6 flex flex-col sm:flex-row justify-center items-center gap-4"
      >
        <input
          type="text"
          id="stockSearch"
          placeholder="Search for a stock (e.g., AAPL)"
          class="px-4 py-2 text-base border border-gray-300 rounded w-72"
        />
        <button
          id="searchButton"
          class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700"
        >
          Search
        </button>
      </section>
      <section class="mb-8">
        <h2 class="text-xl font-semibold mb-2">Stock Information</h2>
        <div
          id="stockDetails"
          class="bg-white p-4 rounded shadow text-gray-700"
        ></div>
      </section>
      <section class="mb-8">
        <h2 class="text-xl font-semibold mb-4">Stock Price Graph</h2>
        <div class="bg-white p-4 rounded shadow" style="height: 400px">
          <canvas id="stockChart" width="800" height="400"></canvas>
        </div>
      </section>    
      <section>
        <h2 class="text-xl font-semibold mb-4">Compare Stocks</h2>
        <div class="overflow-x-auto">
          <table
            class="min-w-full bg-white border border-gray-200 text-center rounded shadow"
          >
            <thead class="bg-gray-100">
              <tr>
                <th class="py-2 px-4 border">Stock</th>
                <th class="py-2 px-4 border">Price</th>
                <th class="py-2 px-4 border">Change</th>
                <th class="py-2 px-4 border">Volume</th>
              </tr>
            </thead>
            <tbody id="stockTable" class="text-gray-700">
            </tbody>
          </table>
        </div>
      </section>
    </main>    -->
      <!-- <script>
      const apiKey = "BGRQ0GBUKRRPK9GC"; // Free tier has limitations (Alpha Vantage API)

      async function fetchStockData(symbol) {
        const response = await fetch(
          `https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=${symbol}&apikey=${apiKey}`
        );
        const data = await response.json();
        return data;
      }

      function displayStockInfo(symbol, data) {
        const timeSeries = data["Time Series (Daily)"];
        const latestDate = Object.keys(timeSeries)[0];
        const latestData = timeSeries[latestDate];
        stockDetails.innerHTML = `
      <p><strong>Symbol:</strong> ${symbol}</p>
      <p><strong>Date:</strong> ${latestDate}</p>
      <p><strong>Open:</strong> $${latestData["1. open"]}</p>
      <p><strong>High:</strong> $${latestData["2. high"]}</p>
      <p><strong>Low:</strong> $${latestData["3. low"]}</p>
      <p><strong>Close:</strong> $${latestData["4. close"]}</p>
      <p><strong>Volume:</strong> ${latestData["5. volume"]}</p>
    `;
      }

      function plotChart(data) {
        const timeSeries = data["Time Series (Daily)"];
        const labels = Object.keys(timeSeries).slice(0, 30).reverse();
        const prices = labels.map((date) =>
          parseFloat(timeSeries[date]["4. close"])
        );

        if (stockChart) stockChart.destroy();

        stockChart = new Chart(ctx, {
          type: "line",
          data: {
            labels,
            datasets: [
              {
                label: "Closing Price",
                data: prices,
                borderColor: "rgb(34,197,94)",
                backgroundColor: "rgba(34,197,94,0.2)",
                fill: true,
                tension: 0.4,
              },
            ],
          },
        });
      }

      searchButton.addEventListener("click", async () => {
        const symbol = stockSearch.value.trim().toUpperCase();
        if (!symbol) return alert("Please enter a stock symbol.");
        const data = await fetchStockData(symbol);
        if (data["Error Message"]) return alert("Invalid symbol or API error.");
        displayStockInfo(symbol, data);
        plotChart(data);
      });

      // Optional: Populate dropdown with trending stocks
      const trendingStocks = ["AAPL", "MSFT", "GOOGL", "TSLA", "AMZN"];
      trendingStocks.forEach((symbol) => {
        const option = document.createElement("option");
        option.value = symbol;
        option.textContent = symbol;
        stockDropdown.appendChild(option);
      });

      loadStockButton.addEventListener("click", async () => {
        const symbol = stockDropdown.value;
        const data = await fetchStockData(symbol);
        if (data["Error Message"]) return alert("Invalid symbol or API error.");
        displayStockInfo(symbol, data);
        plotChart(data);
      });
    </script> -->