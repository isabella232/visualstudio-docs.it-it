---
title: 'Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16fec4cf6150fe0711812d9fabe57fc667e36eef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993500"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. Apportare la modifica nel **DSL Explorer**, nelle proprietà del progetto di pacchetto Dsl e le informazioni di assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1. Nelle **DSL Explorer**, selezionare la **Dsl** nodo.

2. Nel **delle proprietà** finestra Modifica il **Namespace** proprietà.

3. Salvare la soluzione e trasformare i modelli.

4. Nel **Project** menu, scegliere **Dsl proprietà**.

   Vengono visualizzate le proprietà per il progetto.

5. Selezionare il **applicazione** scheda.

6. Modifica il **spazio dei nomi predefinito** proprietà per il nuovo nome dello spazio dei nomi.

7. Se inoltre si desidera modificare il nome dell'assembly, modificare il **proprietà nome Assembly.**

8. Se è stato modificato il nome dell'Assembly, aprire DslPackage\Package.tt e aggiornare questa riga:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se è stato scritto codice personalizzato, assicurarsi di modificare i riferimenti di spazio dei nomi e classe nei file di codice.

10. Reimpostare l'istanza sperimentale di Visual Studio.

    1. Eliminare **\Users\\**_{nome}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. Nella finestra di Windows **avviare** menu, scegliere **tutti i programmi** > **Microsoft Visual Studio 2010 SDK** > **strumenti**  >  **Reimpostare l'istanza sperimentale**.

11. Nel **compilare** menu, scegliere **Ricompila soluzione**.

## <a name="see-also"></a>Vedere anche

[Glossario sugli strumenti di linguaggio specifico di dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)