---
title: 'Avviso: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non è possibile copiare la directory di esecuzione perché sovrascriverebbe il riferimento &#39;file. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8865a1509016a51f30913e51c06e2bcc63912013
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694236"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Avviso: la dipendenza &#39;file&#39; nel progetto &#39;progetto&#39; non è possibile copiare la directory di esecuzione perché sovrascriverebbe il riferimento &#39;file.&#39;
Esiste un conflitto tra le dipendenze. Per eseguire l'applicazione, è necessario copiare più di un file di assembly distinto con lo stesso nome nella directory bin. La directory di esecuzione è in grado di risolvere il conflitto, poiché una delle dipendenze è un riferimento primario.  
  
 Facendo doppio clic sull'elemento Elenco attività si passerà al nodo del riferimento primario in conflitto.  
  
 Questo avviso viene visualizzato in presenza di un conflitto di dipendenza che si è cercato di risolvere aggiungendo una delle dipendenze in conflitto come un riferimento. Oppure si può avere un riferimento alla versione 1 al quale si è aggiunto un secondo riferimento che a sua volta fa riferimento alla versione 2 del primo riferimento.  
  
 Questo errore si verifica perché i progetti nella soluzione hanno riferimenti reciproci, che tuttavia sono stati creati come riferimenti a file (usando il pulsante **Sfoglia** nella finestra di dialogo [Aggiungi riferimento](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ) piuttosto che come riferimenti da progetto a progetto (usando la scheda **Progetto** nella finestra di dialogo **Aggiungi riferimento** ). Il vantaggio di un riferimento da progetto a progetto è che si crea una dipendenza tra i progetti nel sistema di compilazione in base alla quale il progetto dipendente viene compilato in caso di modifica dall'ultima volta in cui è stato compilato il progetto di riferimento. Un riferimento a file non crea una dipendenza di compilazione ed è quindi possibile compilare il progetto di riferimento senza compilare il progetto dipendente, con la possibilità che il riferimento diventi obsoleto. Un progetto può fare riferimento a una versione di compilazione precedente. Ciò potrebbe comportare l'esigenza di varie versioni di una singola DLL nella directory bin, il che non è possibile, e verrà quindi visualizzato questo messaggio di errore.  
  
 Tale messaggio viene visualizzato ogni volta che si verifica un conflitto nella directory bin e l'applicazione potrebbe non funzionare correttamente. Anche se si è aggirato il problema, questo avviso viene ancora visualizzato perché il sistema di progetto non può determinare se la versione di una dipendenza funzionerà correttamente con tutti i componenti.  
  
 **Per correggere questo errore**  
  
- Copiare uno (o zero) file di assembly nella directory bin, operazione che può essere eseguita inserendo i file di assembly nella Global Assembly Cache. La Global Assembly Cache consente di risolvere i conflitti nel nome del file. Non vengono eseguite copie locali del file di assembly dal momento che Common Language Runtime sa come trovare assembly nella Global Assembly Cache. Per altre informazioni, vedere [Working with Assemblies and the Global Assembly Cache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) e [Error: the dependency 'file' in project 'project' cannot be copied to the run directory because it would conflict with dependency 'file'](/visualstudio/misc/error-dependency-file?view=vs-2015).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Procedura: Creare e rimuovere dipendenze del progetto](../ide/how-to-create-and-remove-project-dependencies.md)