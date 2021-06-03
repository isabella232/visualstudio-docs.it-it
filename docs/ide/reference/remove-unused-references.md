---
title: Rimuovere i riferimenti inutilizzati
description: Informazioni su come pulire i riferimenti al progetto e i pacchetti NuGet che non sono usati con il nuovo comando Rimuovi riferimenti inutilizzati.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352094"
---
# <a name="remove-unused-references"></a>Rimuovere i riferimenti inutilizzati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di rimuovere i riferimenti inutilizzati.

**Quando:** Si vuole pulire i riferimenti al progetto e i pacchetti NuGet che non hanno alcun utilizzo. 

**Perché:** La rimozione dei riferimenti al progetto senza utilizzo consente di risparmiare spazio e ridurre il tempo di avvio dell'applicazione, perché il caricamento di ogni modulo richiede tempo ed evita che i metadati di caricamento del compilatore non verranno mai usati.

## <a name="how-to"></a>Procedure

1. Fare clic con il pulsante destro del mouse sul nome di un progetto o sul nodo delle dipendenze Esplora soluzioni.

2. Selezionare **Rimuovi riferimenti inutilizzati.**

    ![Comando Rimuovi riferimenti inutilizzati](media/remove-unused-references-command.png)

3. Verrà **visualizzata la finestra di dialogo** Rimuovi riferimenti inutilizzati in cui sono visualizzati i riferimenti che non hanno alcun utilizzo nel codice sorgente. I riferimenti inutilizzati verranno pre-selezionati per la rimozione con un'opzione per mantenere i riferimenti selezionando `Keep` dall'elenco a discesa Azione.

    ![Finestra di dialogo Rimuovi riferimenti inutilizzati](media/remove-unused-references-dialog.png)

5. Fare clic `Apply` per rimuovere i riferimenti selezionati. 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)