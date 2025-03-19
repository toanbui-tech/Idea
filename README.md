# Idea

## App [Ezy Calculator]:
1. Tính toán khoản vay cơ bản:
- Nhập số tiền vay, lãi suất, thời gian vay.
- Hiển thị số tiền phải trả hàng tháng.

  ```js
  import { useState } from "react";

  export default function LoanCalculator() {
    const [amount, setAmount] = useState(1000000);
    const [rate, setRate] = useState(5);
    const [years, setYears] = useState(1);
    const [monthlyPayment, setMonthlyPayment] = useState(0);
  
    const calculateLoan = () => {
      const monthlyRate = rate / 100 / 12;
      const numberOfPayments = years * 12;
      const payment =
        (amount * monthlyRate) / (1 - Math.pow(1 + monthlyRate, -numberOfPayments));
      setMonthlyPayment(payment);
    };
  
    return (
      <div className="p-4 max-w-md mx-auto bg-white shadow-lg rounded-2xl">
        <h2 className="text-xl font-bold mb-4">Loan Calculator</h2>
        <div className="mb-2">
          <label className="block font-medium">Loan Amount</label>
          <input
            type="number"
            value={amount}
            onChange={(e) => setAmount(Number(e.target.value))}
            className="w-full p-2 border rounded"
          />
        </div>
        <div className="mb-2">
          <label className="block font-medium">Interest Rate (%)</label>
          <input
            type="number"
            value={rate}
            onChange={(e) => setRate(Number(e.target.value))}
            className="w-full p-2 border rounded"
          />
        </div>
        <div className="mb-2">
          <label className="block font-medium">Loan Term (Years)</label>
          <input
            type="number"
            value={years}
            onChange={(e) => setYears(Number(e.target.value))}
            className="w-full p-2 border rounded"
          />
        </div>
        <button
          onClick={calculateLoan}
          className="w-full bg-blue-500 text-white p-2 rounded mt-4 hover:bg-blue-600"
        >
          Calculate
        </button>
        {monthlyPayment > 0 && (
          <div className="mt-4 p-3 bg-green-100 text-green-800 rounded">
            <strong>Monthly Payment:</strong> ${monthlyPayment.toFixed(2)}
          </div>
        )}
      </div>
    );
  }
```
