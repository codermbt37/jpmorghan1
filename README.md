# jpmorghan1
software engineering 
From e36af275d64854a7e849c32f5e58390fd6126ab1 Mon Sep 17 00:00:00 2001
From: brahma_teja <manepallibrahmateja6@gmail.com>
Date: Sat, 30 Jul 2022 08:12:42 +0000
Subject: [PATCH] Create-Patch-File


---
 client3.py | 21 ++++++++++++---------
 1 file changed, 12 insertions(+), 9 deletions(-)

diff --git a/client3.py b/client3.py
index e88878a..4bdf5c7 100644
--- a/client3.py
+++ b/client3.py
@@ -35,25 +35,28 @@ def getDataPoint(quote):
 	stock = quote['stock']
 	bid_price = float(quote['top_bid']['price'])
 	ask_price = float(quote['top_ask']['price'])
-	price = bid_price
+	price = (bid_price+ask_price)/2
 	return stock, bid_price, ask_price, price
 
 def getRatio(price_a, price_b):
-	""" Get ratio of price_a and price_b """
-	""" ------------- Update this function ------------- """
-	""" Also create some unit tests for this function in client_test.py """
-	return 1
+ """ Get ratio of price_a and price_b """
+ """ ------------- Update this function ------------- """
+ """ Also create some unit tests for this function in client_test.py """
+ if  (price_b==0):
+ #when price_b is 0 avoid throwing ZeroDivisionError
+          return
+ return  price_a/price_b
 
     # Main
 if __name__ == "__main__":
 
 	# Query the price once every N seconds.
-	for _ in iter(range(N)):
+	for _ in range(N):
 		quotes = json.loads(urllib.request.urlopen(QUERY.format(random.random())).read())
 
 		""" ----------- Update to get the ratio --------------- """
-		for quote in quotes:
+prices={}    
+for quote in quotes:
 			stock, bid_price, ask_price, price = getDataPoint(quote)
 			print ("Quoted %s at (bid:%s, ask:%s, price:%s)" % (stock, bid_price, ask_price, price))
-
-		print ("Ratio %s" % getRatio(price, price))
+print ("Ratio %s" % getRatio(price, price))
-- 
2.17.1
