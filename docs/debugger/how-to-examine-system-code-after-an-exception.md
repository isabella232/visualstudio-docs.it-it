---
title: Esaminare il codice di sistema dopo un'eccezione | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b9467ce7001f0061c20a5097220bd93b24937db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894034"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Procedura: Esaminare il codice di sistema dopo un'eccezione
Quando si verifica un'eccezione, potrebbe essere necessario esaminare il codice di una chiamata al sistema per determinare la causa dell'eccezione. Nella procedura riportata di seguito viene illustrato come determinare la causa se non sono disponibili simboli caricati per il codice di sistema o se Just My Code è attivato.

### <a name="to-examine-system-code-following-an-exception"></a>Per esaminare il codice di sistema dopo un'eccezione

1. Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse e quindi fare clic su **Mostra codice esterno**.

     Se Just My Code non è attivato, questa opzione non è disponibile nel menu di scelta rapida e il codice di sistema viene visualizzato per impostazione predefinita.

2. Fare clic con il pulsante destro del mouse sui frame di codice esterni presenti nella finestra **Stack di chiamate**.

3. Selezionare **Carica simboli da** e quindi fare clic su **Server dei simboli Microsoft**.

    1. Se Just My Code è attivato, viene visualizzata una finestra di dialogo indicante che Just My Code è stato disabilitato. Tale operazione è necessaria per eseguire le chiamate di sistema.

    2. Viene visualizzata la finestra di dialogo **Download dei simboli pubblici**. La finestra viene chiusa al termine del download.

4. È ora possibile esaminare il codice di sistema nella finestra **Stack di chiamate** e in altre finestre. Ad esempio, è possibile fare doppio clic su un frame dello stack di chiamate per visualizzare il codice nella finestra **Disassembly** o nella finestra origine.

## <a name="see-also"></a>Vedere anche
- [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)