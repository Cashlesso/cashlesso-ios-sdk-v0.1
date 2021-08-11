# cashlesso-ios-sdk-v0.1
IOS SDK

Steps to make Payment Request and handle Response

 **Step 1) create request dictionary**
  
```Swift

        let reqDict:[“String”:”String”] = ["AMOUNT" : "100",
         "CURRENCY_CODE" : "356",
         "CUST_CITY" : "Demo City",
         "CUST_COUNTRY" : "Demo Country",
         "CUST_EMAIL" : "demo@cashlesso.co.in",
         "CUST_NAME" : "Demo Merchant",
         "CUST_PHONE" : "1234567890",
         "CUST_SHIP_CITY" : "Demo Ship City",
         "CUST_SHIP_COUNTRY" : "Demo Ship Country",
         "CUST_SHIP_EMAIL" : "demoship@cashlesso.com",
         "CUST_SHIP_NAME" : "Demo Ship Customer",
         "CUST_SHIP_PHONE" : "0123456789",
         "CUST_SHIP_STATE" : "Demo Ship State",
         "CUST_SHIP_STREET_ADDRESS1" : "Demo Ship Address1",
         "CUST_SHIP_STREET_ADDRESS2" : "Demo Ship Address2",
         "CUST_SHIP_ZIP" : "Demo Ship Zip Code",
         "CUST_STATE" : "Demo State",
         "CUST_STREET_ADDRESS1" : "Demo Address1",
         "CUST_STREET_ADDRESS2" : "Demo Address2",
         "CUST_ZIP" : "Demo Zip Code",
         "ORDER_ID" : "SIGORD220111111111",
         "PAY_ID" : "YOUR_PAY_ID",
         "PRODUCT_DESC" : "Demo Product",
         "RETURN_URL" :  "Your_RETURL_URL"]

```

  **Step 2) create CashlessoPGVC object**
      
```Swift        
         var webVC: CashlessoPGVC!

```

  **Step 3) configure CashlessoPGVC object**
  
```Swift

        paymentVC = CashlessoPGVC(params: reqDict, secretKey: "your_Secret_key", titleString: "Payment", 
        titleColor: .yellow, navigationBarColor: .blue, isUAT: true)
        
```
 **Step 4) navigation push to webVC**

```Swift

        webVC.delegate = self
 
 ```
 
 **Step 5) navigation push to webVC**
 
 ```Swift
 
        //"CashlessoPGVC needs to be contained in a UINavigationController."
         self.navigationController?.pushViewController(paymentVC, animated: true)
 
 ```
 
 **Step 6) handle CashlessoPGDelegate**
 
 ```Swift
 
        extension ViewController: CashlessoPGDelegate{

        //triggers when there's success/failure response

            func postresponse(data: [String : Any]) {
                print("response data:  \(data)")
            }

         //triggers payment gateway page starts loading

            func didPGStartLoading() {
                print("page load started")
            }

         //triggers payment gateway page finish loading

            func didPGFinishLoading(success: Bool) {
                print("page finished loading")
            }    
        }

```



