---
title: 'Procedura: Modificare il Namespace di un linguaggio specifico di dominio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e86fa8f220cdd31beae12e050a1cbaa592624a74
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690558"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procedura: Modificare lo spazio dei nomi di un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare lo spazio dei nomi di un linguaggio specifico di dominio. È necessario apportare le modifiche nel **DSL Explorer**, nelle proprietà del progetto di pacchetto Dsl e le informazioni di assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Per modificare lo spazio dei nomi di un linguaggio specifico di dominio  
  
1. Nelle **DSL Explorer**, fare clic sui **Dsl** nodo.  
  
2. Nel **delle proprietà** finestra Modifica il **Namespace** proprietà.  
  
3. Salvare la soluzione e trasformare i modelli.  
  
4. Nel **Project** menu, fare clic su **Dsl proprietà**.  
  
     Vengono visualizzate le proprietà per il progetto.  
  
5. Fare clic sulla scheda **Applicazione** .  
  
6. Modifica il **spazio dei nomi predefinito** proprietà per il nuovo nome dello spazio dei nomi.  
  
7. Se inoltre si desidera modificare il nome dell'assembly, modificare il **proprietà nome Assembly.**  
  
8. Se è stato modificato il nome dell'Assembly, aprire DslPackage\Package.tt e aggiornare questa riga:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se è stato scritto codice personalizzato, assicurarsi di modificare i riferimenti di spazio dei nomi e classe nei file di codice.  
  
10. Reimpostare l'istanza sperimentale di Visual Studio.  
  
    1. Eliminare **\Users\\**_{nome}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2. Nella finestra di Windows **avviare** menu, scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**, **reimpostare il Istanza sperimentale**.  
  
11. Nel **compilare** menu, scegliere **Ricompila soluzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
