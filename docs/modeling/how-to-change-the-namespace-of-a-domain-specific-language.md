---
title: 'Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio'
description: Fornisce informazioni su come modificare lo spazio dei nomi di un linguaggio specifico di dominio.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: db9043c2a4c5abd19c839d2586709412d7607019
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387307"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. Apportare la modifica in **DSL Explorer,** nelle proprietà del progetto pacchetto Dsl e nelle informazioni sull'assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1. In **DSL Explorer** selezionare il **nodo Dsl.**

2. Nella finestra **Proprietà** modificare la proprietà **Spazio dei** nomi .

3. Salvare la soluzione e trasformare i modelli.

4. Scegliere **Proprietà** **Dsl dal** menu Progetto .

   Verranno visualizzate le proprietà per il progetto.

5. Selezionare la **scheda** Applicazione.

6. Modificare la **proprietà Spazio dei nomi** predefinito con il nuovo nome dello spazio dei nomi.

7. Se si vuole modificare anche il nome dell'assembly, modificare la **proprietà Nome assembly .**

8. Se è stato modificato il nome dell'assembly, aprire DslPackage\Package.tt e aggiornare questa riga:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se è stato scritto codice personalizzato, assicurarsi di modificare i riferimenti allo spazio dei nomi e alla classe nei file di codice.

10. Reimpostare l'Visual Studio sperimentale.

    1. Eliminare **\Users \\**_{your name}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**.

    2. Nel menu **Start di** Windows scegliere Tutti **i** programmi  >  **Microsoft Visual Studio 2010 SDK** Tools Reset the Experimental Instance ( Reimposta istanza  >    >  **sperimentale).**

11. Scegliere **Ricompila** **soluzione dal** menu Compila .

## <a name="see-also"></a>Vedi anche

[Glossario degli strumenti del linguaggio specifico di dominio](/previous-versions/bb126564(v=vs.100))