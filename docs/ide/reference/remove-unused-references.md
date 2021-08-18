---
title: Rimuovere i riferimenti inutilizzati
description: Informazioni su come pulire i riferimenti al progetto e NuGet pacchetti che non hanno alcun utilizzo con il nuovo comando Rimuovi riferimenti inutilizzati.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 19fe9badea98eafa040557d6d373ad72df588229
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143599"
---
# <a name="remove-unused-references"></a>Rimuovere i riferimenti inutilizzati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** Consente di rimuovere i riferimenti inutilizzati.

**Quando:** Si vuole pulire i riferimenti al progetto e NuGet pacchetti che non hanno alcun utilizzo. 

**Perché:** La rimozione dei riferimenti al progetto che non hanno alcun utilizzo consente di risparmiare spazio e ridurre il tempo di avvio dell'applicazione, perché richiede tempo per caricare ogni modulo ed evita che i metadati del compilatore carichino i metadati che non verranno mai usati.

## <a name="how-to"></a>Procedure

1. Fare clic con il pulsante destro del mouse su un nome di progetto o su un nodo delle dipendenze Esplora soluzioni.

2. Selezionare **Rimuovi riferimenti inutilizzati**.

    ![Comando Rimuovi riferimenti inutilizzati](media/remove-unused-references-command.png)

3. Verrà **visualizzata la finestra di dialogo** Rimuovi riferimenti inutilizzati che visualizza i riferimenti che non hanno alcun utilizzo nel codice sorgente. I riferimenti inutilizzati verranno pre-selezionati per la rimozione con un'opzione per mantenere i riferimenti selezionando `Keep` dall'elenco a discesa Azione.

    ![Finestra di dialogo Rimuovi riferimenti inutilizzati](media/remove-unused-references-dialog.png)

5. Fare `Apply` clic per rimuovere i riferimenti selezionati. 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)