---
layout: post
title: using-custvendagingstatistics-to-get-aging-info-from-ax
---
Took me some time but I was able to track down how to get aging
information out of AX through it’s Business Connector. I’m putting this
here as a reminder of how to get it done.

    using (var cust = ax.CreateAxaptaRecord("CustTable")){    //Find the customer you want to get aging info for    ax.ExecuteStmt(String.Format(@"SELECT * FROM %1 WHERE %1.AccountNum == '{0}'", acctNum), cust);    while (cust.Found)    {        var custVendStats = ax.CallStaticClassMethod("CustVendAgingStatistics", "construct",         cust, //Customer record        "", //Aging bucket name goes here         2) //Document type        as AxaptaObject;        custVendStats.Call("calcStatistic");        var accountSum = custVendStats.Call("TmpAccountsum") as AxaptaRecord;         while (accountSum.Next()) //the secret to getting results is to call .Next() before reading.        {            //Do something super interesting with the aging.                    }         cust.Next();    }}
