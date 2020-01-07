---
title: Debug in pacchetti NuGet con collegamento all'origine
description: Questo articolo descrive la funzionalità di collegamento all'origine in Visual Studio per Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451489"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Debug in pacchetti NuGet con collegamento all'origine

La tecnologia di collegamento all'origine consente il debug del codice sorgente degli assembly .NET da NuGet fornito. PDB con collegamenti a file di origine. Il collegamento all'origine viene eseguito quando gli sviluppatori creano il pacchetto NuGet e incorporano i metadati del controllo del codice sorgente all'interno degli assembly e del pacchetto. Quando il collegamento all'origine è abilitato in Visual Studio per Mac, l'IDE rileva se sono disponibili file di origine per i pacchetti installati. In Visual Studio per Mac sarà quindi possibile eseguirne il download, in modo da consentire l'esecuzione del codice del pacchetto. Il collegamento all'origine funziona anche con il codice della libreria di classi base mono per i progetti Novell, consentendo di eseguire l'istruzione .NET Framework codice. Il collegamento all'origine fornisce i metadati di controllo del codice sorgente per creare una straordinaria esperienza di debug.

> [!NOTE]
> Visual Studio per Mac attualmente non supporta i server di simboli. Per questo motivo, il collegamento all'origine con i metadati ospitati nei server di simboli non è supportato.

## <a name="enable-source-link"></a>Abilita collegamento all'origine

Per abilitare il collegamento di origine in Visual Studio per Mac, passare a **Visual Studio > preferenze... > Projects > debugger** e verificare che la casella di controllo **Esegui codice esterno** sia selezionata.

![Screenshot della finestra di dialogo delle Preferenze visualizzazione della casella di controllo Esegui codice esterno](media/source-link1.png)

È possibile modificare l'impostazione in **Scarica codice esterno** in base alle proprie preferenze:
* Ask: Visual Studio per Mac richiederà di scaricare il codice esterno
* Always: Visual Studio per Mac scaricherà automaticamente il codice esterno
* Mai: non Visual Studio per Mac scaricare il codice esterno correlato

Per impostazione predefinita, è selezionata l'opzione **Ask** . Quando viene trovato codice esterno per un pacchetto NuGet, verrà visualizzato il messaggio seguente:

![Screenshot della richiesta visualizzata quando viene trovato codice esterno per un pacchetto NuGet](media/source-link2.png)


## <a name="see-also"></a>Vedere anche

- [Repository GitHub](https://github.com/dotnet/sourcelink/blob/master/README.md) per il collegamento all'origine
- [Documentazione .NET](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) sul collegamento di origine e per altre informazioni su come aggiungere il supporto per il collegamento all'origine ai pacchetti
