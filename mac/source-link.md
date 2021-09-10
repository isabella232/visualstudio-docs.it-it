---
title: Debug in pacchetti NuGet con collegamento all'origine
description: Questo articolo descrive la funzionalità Collegamento all'origine in Visual Studio per Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964614"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debug in pacchetti NuGet con collegamento all'origine

La tecnologia di collegamento all'origine consente il debug del codice sorgente di assembly .NET NuGet che fornisce . File PDB con collegamenti ai file di origine. Il collegamento all'origine viene eseguito quando gli sviluppatori creano il NuGet e incorporano i metadati del controllo del codice sorgente all'interno degli assembly e del pacchetto. Quando collegamento all'origine è abilitato in Visual Studio per Mac, l'IDE rileverà se i file di origine sono disponibili per i pacchetti installati. Visual Studio per Mac offrirà quindi di scaricarli, in modo da consentire di eseguire il codice del pacchetto un'istruzione alla volta. Il collegamento all'origine funziona anche con il codice della libreria di classi base Mono per i progetti Xamarin, consentendo di eseguire un'istruzione .NET Framework codice. Il collegamento all'origine fornisce i metadati di controllo del codice sorgente per creare una straordinaria esperienza di debug.

> [!NOTE]
> Visual Studio per Mac attualmente non supporta i server di simboli. Per questo problema, il collegamento all'origine con metadati ospitati nei server di simboli non è supportato.

## <a name="enable-source-link"></a>Abilita collegamento all'origine

Per abilitare il collegamento all'origine Visual Studio per Mac, passare Visual Studio > **Preferenze... > Projects > Debugger (Progetti** > Debugger) e verificare che la casella di controllo **Step into external code** (Istruzione nel codice esterno) sia selezionata.

![Screenshot della finestra di dialogo delle preferenze che mostra la casella di controllo Istruzione nel codice esterno](media/source-link1.png)

È possibile modificare l'impostazione in **Scarica codice esterno in** base alle proprie preferenze:
* Chiedi: Visual Studio per Mac verrà richiesto di scaricare il codice esterno
* Sempre: Visual Studio per Mac scarica automaticamente il codice esterno
* Mai: Visual Studio per Mac non scaricherà il codice esterno correlato

Per impostazione predefinita, **l'opzione Chiedi** è selezionata. Quando viene trovato codice esterno per un pacchetto NuGet seguente:

![Screenshot della richiesta visualizzata quando viene trovato codice esterno per un NuGet pacchetto](media/source-link2.png)


## <a name="see-also"></a>Vedi anche

- Repository [del collegamento GitHub origine](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentazione di .NET](/dotnet/standard/library-guidance/sourcelink) sul collegamento all'origine e per altre informazioni su come aggiungere il supporto del collegamento all'origine ai pacchetti