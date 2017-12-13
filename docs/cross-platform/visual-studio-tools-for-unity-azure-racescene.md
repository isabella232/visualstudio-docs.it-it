---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - RaceScene | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 304fb69ab6e5da058cd3d2a4d6de202fa042b8f9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="racescene-explanation"></a>Spiegazione di RaceScene

RaceScene usa [risorse standard](https://www.assetstore.unity3d.com/en/#!/content/32351) di Unity per creare le funzioni di base del gioco di corsa e il livello. In questa sezione vengono illustrati alcuni GameObject pertinenti e gli script relativi nell'ordine in cui sono elencati nella gerarchia di RaceScene, come visualizzato nello screenshot seguente.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** proviene dal pacchetto delle risorse standard **Cameras** (Fotocamere). Le proprietà di controllo sono state ottimizzate in modo che seguano il veicolo a una velocità appropriata.

## <a name="levelgeometry"></a>LevelGeometry

Il prefab LevelGeometry è un GameObject vuoto usato per l'organizzazione. I suoi GameObject figlio compongono lo spazio di gioco. I piani, le pareti, le rampe e gli ostacoli vengono creati da prefab nel pacchetto di risorse standard **Prototyping** (Prototipi).

**Nota importante:** perché un oggetto possa essere sottoposto a test degli impatti registrabili in Azure, all'oggetto deve essere applicato il tag **Wall** (Parete).

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

Il prefab **Car** (Auto) proviene dal pacchetto di risorse standard **Vehicles** (Veicoli). L'unica modifica è l'aggiunta del componente di script **RecordCrashInfo**.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Questo script verifica l'esistenza di impatti in `OnCollisionEnter` e li registra in un elenco. `crashRecordingCooldown` e `crashRecordingMinVelocity` limitano ciò che il gioco considera un impatto per mantenere un set di dati pertinente.

Quando viene generato l'evento `RaceFinished`, `UploadNewCrashDataAsync` invia ogni impatto dell'elenco alla tabella semplice CrashInfo in Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

Il livello ha quattro GameObject con il componente script **Checkpoint**. I checkpoint assicurano che il giocatore non possa completare la corsa procedendo in senso contrario lungo il percorso. I checkpoint rilevano anche quando il giocatore termina la corsa. A questo punto viene chiamato l'evento `RaceFinished`.

## <a name="invisible-collision"></a>Collisione invisibile

Cubi primitivi standard con i relativi componenti MeshRenderer disabilitati vengono usati per generare collisioni invisibili e mantenere il giocatore nel percorso corretto. Viene anche applicato il materiale di fisica **Bouncy** per assicurarsi che le auto volanti rimbalzino sulle pareti invisibili in modo soddisfacente e per evitare che il giocatore colpisca una parete invisibile, vi scorra sopra e atterri sopra una parete visibile.

## <a name="recordhighscore"></a>RecordHighScore

Questo script verifica se il giocatore ha raggiunto un nuovo punteggio record. In caso affermativo, viene visualizzata la finestra `enterNamePopup`, che consente di immettere il proprio nome e fare clic su **Submit** (Invia).

Dopo che il nome del giocatore è stato inviato, viene chiamato `UploadNewHighScoreAsync` e il nuovo punteggio record viene inviato alla tabella semplice HighScoreInfo in Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Passaggio successivo

* [Spiegazione di HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md).
