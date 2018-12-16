# wemoinsight
just a simple -though ugly- way to get power consumption over a wemo insight switch


this is a simple modification of rich@netmagi.com's script that can be found here : http://moderntoil.com/?p=839
I wanted to get the GetPower Property which is mentionned here and there. 
I never managed to get this stuff working. 

I found an alternate solution which is to get the InsightParams from the wemo insight API.
the result is a string which looks like that : 
1|1544988731|3|38049|456580|1209600|361|1430400|657939175|7107245804.000000|8000

I was able to identify the meaning of some -not all- fields
field 1 : 1 is the position of the switch (1-ON |0-OFF)
field 2 : 1544988731 is the date in secondes since 1970/01/01
field 3 : unknown
field 4 : 38049 Today's activity in sec
field 5 : 456580 Total activity in sec
field 6 : 1209600 unknown
field 7 : 361 unknown
field 8 : unknown 
field 9 :  657939175 Energy Today that's our consumption ! (on mwh -> to be divided by 60000 to get the Energy Today 
field 10 : 7107245804 Total Engery (since when? )
field 11 : unknown 

then the only thing to do is to get the InsightParam, get the field n# 9  and divide it by 60000
