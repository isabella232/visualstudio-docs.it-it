---
title: 'Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio'
description: Vengono fornite informazioni su come modificare lo spazio dei nomi di un linguaggio specifico di dominio.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 66ce1219f3a18c65e23c2ddc420449a0d8bc7b3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157488"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. Apportare la modifica in **Esplora DSL**, nelle proprietà del progetto pacchetto Dsl e nelle informazioni sull'assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1. In **Esplora DSL** selezionare il **nodo Dsl.**

2. Nella finestra **Proprietà** modificare la proprietà **Spazio dei** nomi .

3. Salvare la soluzione e trasformare i modelli.

4. Nel menu **Project** scegliere **Proprietà Dsl**.

   Vengono visualizzate le proprietà per il progetto.

5. Selezionare la **scheda** Applicazione.

6. Modificare la **proprietà Spazio dei nomi** predefinito con il nuovo nome dello spazio dei nomi.

7. Se si vuole modificare anche il nome dell'assembly, modificare la **proprietà Nome assembly.**

8. Se è stato modificato il nome dell'assembly, aprire DslPackage\Package.tt aggiornare questa riga:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se è stato scritto codice personalizzato, assicurarsi di modificare i riferimenti allo spazio dei nomi e alla classe nei file di codice.

10. Reimpostare l'Visual Studio sperimentale.

    1. Eliminare **\Users \\**_{your name}_**\AppData\Local\Microsoft\VisualStudio \\ \* Exp**.

    2. Nel menu **Windows Start** scegliere Tutti i  >  **programmi Microsoft Visual Studio 2010 SDK** Tools Reset the Experimental Instance (Reimposta istanza  >    >  **sperimentale).**

11. Scegliere **Ricompila** **soluzione dal** menu Compila .

## <a name="see-also"></a>Vedi anche

[Glossario degli strumenti del linguaggio specifico di dominio](/previous-versions/bb126564(v=vs.100))