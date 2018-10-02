---
title: 'Errore: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non può essere copiato nella directory di esecuzione perché genererebbe un conflitto con la dipendenza &#39;file&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 6f571ec21094a28077f63bf86d4afe97af5429dd
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590454"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Errore: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non può essere copiato nella directory di esecuzione perché genererebbe un conflitto con la dipendenza &#39;file&#39;
Esiste un conflitto tra i riferimenti. Per eseguire l'applicazione, vengono copiate più dipendenze distinte con lo stesso nome di file nella directory bin. La directory di esecuzione non riesce a risolvere il conflitto perché nessuna delle dipendenze è un riferimento primario.  
  
 Questo errore impedirà la riuscita della compilazione.  
  
 Facendo doppio clic su questa voce dell'Elenco attività si passa al nodo dei riferimento del progetto in cui il conflitto si è verificato.  
  
 **Per correggere questo errore**  
  
-   Fare in modo che uno degli assembly sia un riferimento diretto del progetto. Un possibile svantaggio di questo approccio è che l'assembly scelto non necessariamente funzionerà con gli assembly che richiedono un'altra versione dell'assembly a cui fanno riferimento.  
  
     \- oppure -  
  
-   Assicurarsi che entrambe le copie dell'assembly abbiano un nome sicuro e si trovino nella Global Assembly Cache. Questo elimina la necessità di copiare gli assembly nella directory bin.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Assembly con nomi sicuri](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Controllo delle versioni degli assembly](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [How to: Create and Remove Project Dependencies](../ide/how-to-create-and-remove-project-dependencies.md) (Procedura: Creare e rimuovere dipendenze di progetto)