---
title: 'Errore: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non può essere copiato nella directory di esecuzione perché genererebbe un conflitto con la dipendenza &#39;file&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7726d615c3495845ffdf73d69ffc7d8fae155272
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688270"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Errore: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non può essere copiato nella directory di esecuzione perché genererebbe un conflitto con la dipendenza &#39;file&#39;
Esiste un conflitto tra i riferimenti. Per eseguire l'applicazione, vengono copiate più dipendenze distinte con lo stesso nome di file nella directory bin. La directory di esecuzione non riesce a risolvere il conflitto perché nessuna delle dipendenze è un riferimento primario.  
  
 Questo errore impedirà la riuscita della compilazione.  
  
 Facendo doppio clic su questa voce dell'Elenco attività si passa al nodo dei riferimento del progetto in cui il conflitto si è verificato.  
  
 **Per correggere questo errore**  
  
- Fare in modo che uno degli assembly sia un riferimento diretto del progetto. Un possibile svantaggio di questo approccio è che l'assembly scelto non necessariamente funzionerà con gli assembly che richiedono un'altra versione dell'assembly a cui fanno riferimento.  
  
     \- oppure -  
  
- Assicurarsi che entrambe le copie dell'assembly abbiano un nome sicuro e si trovino nella Global Assembly Cache. Questo elimina la necessità di copiare gli assembly nella directory bin.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Assembly con nomi sicuri](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Controllo delle versioni degli assembly](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Procedura: Creare e rimuovere dipendenze del progetto](../ide/how-to-create-and-remove-project-dependencies.md)