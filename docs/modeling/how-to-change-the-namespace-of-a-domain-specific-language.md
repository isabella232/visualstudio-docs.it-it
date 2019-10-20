---
title: 'Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653757"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. Apportare le modifiche in **DSL Explorer**, nelle proprietà del progetto di pacchetto DSL e nelle informazioni sull'assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1. In **DSL Explorer**selezionare il nodo **DSL** .

2. Nella finestra **Proprietà** modificare la proprietà **spazio dei nomi** .

3. Salvare la soluzione e trasformare i modelli.

4. Scegliere **Proprietà DSL**dal menu **progetto** .

   Verranno visualizzate le proprietà del progetto.

5. Selezionare la scheda **applicazione** .

6. Modificare la proprietà **spazio dei nomi predefinito** sul nuovo nome dello spazio dei nomi.

7. Se si desidera modificare anche il nome dell'assembly, modificare la **proprietà nome assembly.**

8. Se il nome dell'assembly è stato modificato, aprire DslPackage\Package.tt e aggiornare la riga seguente:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se è stato scritto codice personalizzato, assicurarsi di modificare lo spazio dei nomi e i riferimenti alle classi nei file di codice.

10. Reimpostare l'istanza sperimentale di Visual Studio.

    1. Eliminare **\Users \\** _{nome}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**.

    2. Dal menu **Start** di Windows scegliere **tutti i programmi**  > **Microsoft Visual Studio 2010 SDK**  > **Tools**  > **reimpostare l'istanza sperimentale**.

11. Scegliere **Ricompila soluzione**dal menu **Compila** .

## <a name="see-also"></a>Vedere anche

[Glossario degli strumenti del linguaggio specifico di dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)