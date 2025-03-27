let price;
let cash = document.getElementById("cash");
let priceInput = document.getElementById("price-input"); 
let displayChangeDue = document.getElementById("change-due");
let purchaseBtn = document.getElementById("purchase-btn");
//let displayCid = document.getElementById("cash-in-drawer");


//let price = 19.5;
let cid = [["PENNY", 1.01],["NICKEL", 2.05],["DIME", 3.1],["QUARTER", 4.25],
           ["ONE", 90],["FIVE", 55],["TEN", 20],["TWENTY", 60],["ONE HUNDRED", 100]];

//all the condes are inside of register()so don't pull anything out of the function//

const register = () => {
  let price = parseFloat(priceInput.value); // Cashier puts in the price of the product into input 
  let cashIn = parseFloat(cash.value); // Cash received from the customer coming in
  
  if (isNaN(price) || price <= 0) { // if the price is not a nummber or equal/smaller than 0 
    alert("Please enter a valid price.");
    return;
  }
  
  let change = Number((cashIn - price).toFixed(2));
  let totalCashInDrawer = Number(cid.reduce((total, sum) => total + sum[1], 0).toFixed(2));
  
  if (cashIn < price) {
    alert("Customer does not have enough money to purchase the item");
    return;
  } else if (cashIn === price) {
    displayChangeDue.innerText = "No change due - customer paid with exact cash";
    return;
  } else if (cash.value === "") {
    return;
  }
  if (change > totalCashInDrawer) {
    displayChangeDue.innerText = "Status: INSUFFICIENT_FUNDS";
    return;
  }
  
  const unit = [100, 20, 10, 5, 1, 0.25, 0.10, 0.05, 0.01];
  const unitNames= ["ONE HUNDRED", "TWENTY", "TEN", "FIVE", "ONE", "QUARTER", "DIME", "NICKEL", "PENNY"];  
//This array matches the unit array by index. Used when displaying the change due.
  
  let changeArr = []; //It will be filled with change amount
  let cid2 = [...cid]; // Just a copy of cid array 
  /*let cid = [["PENNY", 1.01],["NICKEL", 2.05],["DIME", 3.1],["QUARTER", 4.25],
           ["ONE", 90],["FIVE", 55],["TEN", 20],["TWENTY", 60],["ONE HUNDRED", 100]];*/
  
  for (let i = 0; i < unit.length; i++) {
    let totalUnit = 0; // This is money amount going out to the customer
      while (change >= unit[i] && cid2[cid2.length - 1 - i][1] > 0) { 
      cid2[cid2.length - 1 - i][1] = Number((cid2[cid2.length - 1 - i][1] - unit[i]).toFixed(2));
      change = Number((change - unit[i]).toFixed(2));
      totalUnit += unit[i];
      } 
      if (totalUnit > 0) {
      changeArr.push([unitNames[i], totalUnit]);
      }
   } if (change > 0) {
    displayChangeDue.innerText = "Status: INSUFFICIENT_FUNDS" ;
    return;
  };
  
  console.log("changeArr:", changeArr);
  
  let remainingChangeinDrawer = cid2.reduce((total, sum) => total + sum[1], 0);
  
  if (remainingChangeinDrawer === 0) {
   displayChangeDue.innerHTML = "Status: CLOSED " + changeArr.map(denomination => `${denomination[0]}: $${denomination[1].toFixed(2)}`).join("<br>");
   cid = cid.map(kind => [kind[0], 0]);
  } 
   else {
   displayChangeDue.innerHTML = `Status:OPEN<br>${changeArr.map(denomination => `${denomination[0]}: $${denomination[1].toFixed(2)}`).join("<br>")}`;
   cid = cid2;
 } displayCashInDrawer();
} // end of register()function

const displayCid = document.getElementById("cash-in-drawer");

const displayCashInDrawer = () => {
  let formattedCid = cid.map(denomination => {
    return `${denomination[0]}: $${denomination[1].toFixed(2)}`;
  }).join("<br>");

  displayCid.innerHTML = formattedCid;
};

// Call this function whenever you want to display the cash-in-drawer


purchaseBtn.addEventListener("click", register);
displayCashInDrawer();
  











