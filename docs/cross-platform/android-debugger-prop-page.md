---
title: "Proprietà del debugger Android (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: a296ea142b13b9bdcda888a7f382de9eeb17a40a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="android-debugger-properties"></a>Proprietà del debugger Android

Proprietà | Descrizione | Scelte
--- | ---| ---
Tipo di debugger | Specifica quale tipo di codice sottoporre al debug. | **Solo nativo**<br>**Solo Java**<br>
Destinazione di debug | Specifica l'emulatore o il dispositivo da usare per il debug. Se non ci sono emulatori in esecuzione, usare il gestore di dispositivi virtuali Android AVD Manager per avviare un dispositivo.
Pacchetto da avviare | Specifica il percorso del file con estensione apk di cui verrà eseguito il debug. Scegliere questa opzione per specificare che durante il debug dell'applicazione deve essere avviato un pacchetto (APK) specifico.
Attività di avvio | L'attività Android da usare per avviare l'applicazione deve essere uguale a quella usata nel manifesto Scegliere Applica per recuperare l'elenco da AndroidManifest.xml e popolarlo dinamicamente.
Percorsi aggiuntivi di ricerca dei simboli | Percorso aggiuntivo di ricerca per i simboli di debug.
Percorsi aggiuntivi di ricerca origine Java | Percorsi di ricerca aggiuntivi per i file di origine Java. (Si applica solo quando il tipo di debugger è solo Java).
