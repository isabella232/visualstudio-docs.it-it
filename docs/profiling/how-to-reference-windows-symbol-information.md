---
title: Fare riferimento alle informazioni sui simboli di Windows | Microsoft Docs
description: Informazioni su come Visual Studio Strumenti di profilatura usare i file di simboli (con estensione pdb) per risolvere i nomi simbolici, ad esempio i nomi delle funzioni nei file binari del programma.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: af194a324840bc3e8b8e67199c7e213d7dca96c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720683"
---
# <a name="how-to-reference-windows-symbol-information"></a>Procedura: Fare riferimento alle informazioni sui simboli di Windows
Gli strumenti di profilatura di Visual Studio usano file di simboli (con estensione *pdb*) per risolvere i nomi simbolici, ad esempio i nomi delle funzioni nei file binari del programma. È possibile seguire questa procedura per scaricare e aggiornare automaticamente i file *pdb* corretti per la versione di Windows nel computer locale.

> [!NOTE]
> Questa impostazione non influisce sui rapporti esistenti. Le informazioni sui simboli saranno presenti solo nei rapporti creati dopo aver specificato il server di simboli.

 Per ulteriori informazioni, vedere [specificare il simbolo (.*PDB*) e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Per usare il server dei simboli Microsoft

1. Creare una cartella per contenere le informazioni sul file di simboli, ad esempio C:\SymbolCache.

2. Scegliere **Opzioni** dal menu **Strumenti**.

     Verrà visualizzata la finestra di dialogo **Opzioni** .

3. Espandere l'albero **Debug** e quindi fare clic su **Simboli**.

4. In **Percorsi dei file di simboli (pdb)** selezionare **Server dei simboli Microsoft**.

5. In **Memorizza nella cache i simboli dai server di simboli in questa directory** digitare il percorso della cartella creata nel passaggio 1, ad esempio:

     **C:\SymbolCache**

     È anche possibile fare clic sul pulsante con i puntini di sospensione (**...**) e quindi selezionare una directory dalla finestra di dialogo **Sfoglia per cartelle**.

## <a name="see-also"></a>Vedere anche
- [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
- [Procedura: serializzare le informazioni sui simboli](../profiling/how-to-serialize-symbol-information.md)
