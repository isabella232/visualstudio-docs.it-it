---
title: Debug in pacchetti NuGet con collegamento di origineDebugging into NuGet packages with Source Link
description: In questo articolo viene descritta la funzionalità di collegamento di origine in Visual Studio per Mac.This article describes the Source Link feature in Visual Studio for Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451489"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debug in pacchetti NuGet con collegamento di origineDebugging into NuGet packages with Source Link

La tecnologia di collegamento di origine consente il debug del codice sorgente degli assembly .NET da NuGet che vengono riprodotti. PDB con collegamenti ai file di origine. Source Link viene eseguito quando gli sviluppatori creano il pacchetto NuGet e incorporano i metadati del controllo del codice sorgente all'interno degli assembly e del pacchetto. Quando collegamento di origine è abilitato in Visual Studio per Mac, l'IDE rileverà se i file di origine sono disponibili per i pacchetti installati. Visual Studio per Mac offrirà quindi di scaricarli, che vi permetterà di eseguire il codice del pacchetto un'istruzione alla volta. Source Link funziona anche con il codice Mono Base Class Library per i progetti Xamarin, consentendo di eseguire anche il codice .NET Framework. Il collegamento all'origine fornisce i metadati di controllo del codice sorgente per creare una straordinaria esperienza di debug.

> [!NOTE]
> Visual Studio per Mac non supporta attualmente i server di simboli. Per questo motivo, il collegamento di origine con metadati ospitati nei server di simboli non è supportato.

## <a name="enable-source-link"></a>Abilita collegamento di origine

Per abilitare collegamento di origine in Visual Studio per Mac, passare a Preferenze di **Visual Studio >... > Progetti > Debugger** e verificare che la casella di controllo Esegui istruzione nel codice **esterno** sia selezionata.

![Screenshot della finestra di dialogo delle preferenze con la casella di controllo Entra nel codice esterno](media/source-link1.png)

Puoi modificare l'impostazione in **Scarica codice esterno** in base alle tue preferenze:
* Chiedi: Visual Studio per Mac ti chiederà di scaricare il codice esterno
* Sempre: Visual Studio per Mac scaricherà automaticamente il codice esterno
* Mai: Visual Studio per Mac non scaricherà il codice esterno correlato

Per impostazione predefinita, **l'opzione Chiedi** è selezionata. Quando viene trovato codice esterno per un pacchetto NuGet, verrà visualizzato il seguente messaggio:

![Screenshot del prompt visualizzato quando viene trovato codice esterno per un pacchetto NuGet](media/source-link2.png)


## <a name="see-also"></a>Vedere anche

- Il [repository GitHub di Collegamento origineThe Source Link GitHub repository](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentazione .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) su Source Link e per ulteriori informazioni su come aggiungere il supporto di Source Link ai pacchetti
