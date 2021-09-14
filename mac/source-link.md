---
title: Debug in pacchetti NuGet con collegamento all'origine
description: Questo articolo descrive la funzionalità Collegamento all'origine in Visual Studio per Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710471"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debug in pacchetti NuGet con collegamento all'origine

La tecnologia di collegamento all'origine consente il debug del codice sorgente di assembly .NET NuGet che vengono forniti. PDB con collegamenti ai file di origine. Il collegamento all'origine viene eseguito quando gli sviluppatori creano NuGet pacchetto e incorporano i metadati del controllo del codice sorgente all'interno di assembly e pacchetto. Quando collegamento all'origine è abilitato in Visual Studio per Mac, l'IDE rileverà se i file di origine sono disponibili per i pacchetti installati. Visual Studio per Mac offrirà quindi di scaricarli, che consentirà di eseguire il codice del pacchetto un'istruzione alla volta. Collegamento al codice sorgente funziona anche con il codice della libreria di classi di base Mono per i progetti Xamarin, consentendo di eseguire .NET Framework codice. Il collegamento all'origine fornisce i metadati di controllo del codice sorgente per creare una straordinaria esperienza di debug.

> [!NOTE]
> Visual Studio per Mac attualmente non supporta i server di simboli. Per questo scopo, collegamento all'origine con metadati ospitati nei server di simboli non è supportato.

## <a name="enable-source-link"></a>Abilita collegamento all'origine

Per abilitare Collegamento all'origine Visual Studio per Mac, passare **Visual Studio > Preferenze... > Projects > Debugger** e verificare che la casella di controllo Step into external **code** (Istruzione nel codice esterno) sia selezionata.

![Screenshot della finestra di dialogo delle preferenze che mostra la casella di controllo Inserisci codice esterno](media/source-link1.png)

È possibile modificare l'impostazione in **Scarica codice esterno** in base alle preferenze:
* Chiedi: Visual Studio per Mac verrà richiesto di scaricare il codice esterno
* Sempre: Visual Studio per Mac il codice esterno verrà scaricato automaticamente
* Mai: Visual Studio per Mac non scaricherà il codice esterno correlato

Per impostazione predefinita, **l'opzione Chiedi** è selezionata. Quando viene trovato il codice esterno per un pacchetto NuGet seguente:

![Screenshot del prompt che viene visualizzato quando viene trovato codice esterno per un NuGet pacchetto](media/source-link2.png)


## <a name="see-also"></a>Vedi anche

- Repository [del GitHub di origine](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentazione di .NET](/dotnet/standard/library-guidance/sourcelink) sul collegamento all'origine e per altre informazioni su come aggiungere il supporto di Collegamento all'origine ai pacchetti