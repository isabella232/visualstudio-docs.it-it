---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - LeaderboardScene | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2127DEBA-9470-490B-BDDF-6F77A5ACC329
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d257d1bdab02128d6c7ac8cebb819bc91ea8df41
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="leaderboardscene-explanation"></a>Spiegazione di LeaderboardScene

LeaderboardScene comprende solo l'interfaccia utente. Nella scena, in Hierarchy (Gerarchia), premere **Alt + clic** sulla **freccia di espansione** accanto al GameObject Canvas per espandere quest'ultimo e i GameObject figlio. Annidato all'interno di Canvas e di Panel (Pannello) si trova il GameObject Leaderboard (tabellone punteggi) con il relativo script.

![GameObject Leaderboard](media/vstu_azure-leaderboard-explanation-image1.png)

## <a name="leaderboard-script"></a>Script di Leaderboard

La classe `Leaderboard` usa una funzione `async Start`, che viene comunque chiamata quando lo script è abilitato, analogamente a una funzione Unity `Start` tipica.

`DownloadHighScoresAsync` usa le funzioni `OrderBy` e `Take` di <a href="https://msdn.microsoft.com/en-us/library/azure/jj554257(v=azure.10).aspx">`IMobileServiceTable`</a> per ordinare i punteggi più alti nella tabella semplice di Azure, ricevendo le voci più alte solo in base alla costante `SizeOfHighScoreList`. Tali voci vengono memorizzate nell'elenco `highScores`.

Viene quindi creata un'istanza del prefab dell'interfaccia utente di riga di punteggio alto per ogni voce nell'elenco.

``` csharp
using Microsoft.WindowsAzure.MobileServices;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;
using System;
using UnityEngine.UI;

public class Leaderboard : MonoBehaviour
{
    [SerializeField]
    private GameObject rowPrefab;

    [SerializeField]
    private Text loadingText;

    public const int SizeOfHighScoreList = 10;
    private static int numberOfAttemptsToLoadData = 3;
    private static IMobileServiceTable<HighScoreInfo> highScoreTable_UseProperty;

    public static IMobileServiceTable<HighScoreInfo> HighScoreTable
    {
        get
        {
            if (highScoreTable_UseProperty == null)
            {
                highScoreTable_UseProperty = AzureMobileServiceClient.Client.GetTable<HighScoreInfo>();
            }

            return highScoreTable_UseProperty;
        }
    }

    public static async Task<List<HighScoreInfo>> GetTopHighScoresAsync()
    {
            return await DownloadHighScoresAsync(true);
    }

    private static async Task<List<HighScoreInfo>> DownloadHighScoresAsync(bool onlyTopEntries)
    {
        List<HighScoreInfo> highScoreList;

        Debug.Log("Downloading high score data from Azure...");

        for (int i = 0; i < numberOfAttemptsToLoadData; i++)
        {
            try
            {
                Debug.Log("Connecting... attempt " + (i + 1));

                if (onlyTopEntries)
                {
                    highScoreList = await HighScoreTable
                        .OrderBy(item => item.Time)
                        .Take(SizeOfHighScoreList)
                        .ToListAsync();
                }
                else
                {
                    highScoreList = await HighScoreTable.ToListAsync();
                }

                Debug.Log("Done downloading high score data.");
                return highScoreList;
            }
            catch (Exception e)
            {
                Debug.Log("Error connecting: " + e.Message);
            }

            if (i == numberOfAttemptsToLoadData - 1)
                Debug.Log("Connection failed. Check logs, try again later.");
            else
                await Task.Delay(500);
        }

        // If we can't successfully download a list from the server,
        // just make a new one to fail more gracefully.
        return highScoreList = new List<HighScoreInfo>();
    }

    private async void Start()
    {
        var highScores = await GetTopHighScoresAsync();

        if (highScores.Count == 0)
        {
            ShowEmptyLeaderboardMessage();
        }
        else
        {
            loadingText.gameObject.SetActive(false);

            foreach (var item in highScores)
            {
                var row = Instantiate(rowPrefab, this.transform).GetComponent<LeaderboardRow>();
                row.HighScoreInfo = item;
            }
        }
    }

    private void ShowEmptyLeaderboardMessage()
    {
        loadingText.text = "The leaderboard is empty!";
    }

    public static async Task DeleteAllEntriesAsync()
    {
       Debug.Log("Deleting leaderboard data...");

        var fullHighScoreList = await DownloadHighScoresAsync(false);

        foreach (var item in fullHighScoreList)
        {
            try
            {
                await HighScoreTable.DeleteAsync(item);
            }
            catch (Exception e)
            {
                Debug.Log("Error deleting leaderboard data: " + e.Message);
            }
        }
    }
}
```