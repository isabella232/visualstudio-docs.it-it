---
title: 'Procedura: modificare lo spazio dei nomi di una Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671725"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: modificare lo spazio dei nomi di un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. È necessario apportare la modifica in **DSL Explorer**, nelle proprietà del progetto di pacchetto DSL e nelle informazioni sull'assembly.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio

1. In **DSL Explorer**fare clic sul nodo **DSL** .

2. Nella finestra **Proprietà** modificare la proprietà **spazio dei nomi** .

3. Salvare la soluzione e trasformare i modelli.

4. Scegliere **Proprietà DSL**dal menu **progetto** .

     Verranno visualizzate le proprietà del progetto.

5. Fare clic sulla scheda **Applicazione** .

6. Modificare la proprietà **spazio dei nomi predefinito** sul nuovo nome dello spazio dei nomi.

7. Se si desidera modificare anche il nome dell'assembly, modificare la **proprietà nome assembly.**

8. Se il nome dell'assembly è stato modificato, aprire DslPackage\Package.tt e aggiornare la riga seguente:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se è stato scritto codice personalizzato, assicurarsi di modificare lo spazio dei nomi e i riferimenti alle classi nei file di codice.

10. Reimpostare l'istanza sperimentale di Visual Studio.

    1. Eliminare **\Users \\** _{nome}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**

    2. Dal menu **Start** di Windows scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**, **reimpostare l'istanza sperimentale**.

11. Scegliere **Ricompila soluzione**dal menu **Compila** .

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
