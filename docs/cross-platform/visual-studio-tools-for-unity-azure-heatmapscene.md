---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - HeatmapScene | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>Spiegazione di HeatmapScene

HeatmapScene contiene un'istanza del prefab **LevelGeometry**. In questo modo le coordinate degli impatti caricati da Azure corrispondono correttamente agli elementi art del livello.

## <a name="heatmap-script"></a>Script di Heatmap

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync`si connette alla tabella semplice CrashInfo in Azure e usa <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx"> `ToListAsync` </a> per aggiungere tutte le voci a un elenco.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` esegue l'iterazione attraverso l'elenco di impatti ricevuto da Azure e crea un prefab indicatore di impatto per ogni voce.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

Lo script `DeleteCrashDataAsync` viene chiamato quando l'utente preme il pulsante **Clear Data** (Cancella dati). Esegue l'iterazione attraverso l'elenco locale di impatti e chiama <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx"> `DeleteAsync` </a> per ogni voce. In questo modo la colonna **Eliminato** nella tabella semplice viene impostata su **true**. `ToListAsync` ignora queste voci eliminate.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Passaggio successivo

* [Spiegazione di LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)