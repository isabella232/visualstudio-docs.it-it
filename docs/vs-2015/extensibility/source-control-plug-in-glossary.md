---
title: Glossario del plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160599"
---
# <a name="source-control-plug-in-glossary"></a>Glossario del plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I termini e le definizioni utili seguenti riguardano la documentazione dell'SDK del plug-in del controllo del codice sorgente.  
  
## <a name="definitions"></a>Definizioni  
 Archiviazione  
 Quando un utente apporta modifiche a una copia di lavoro, è necessario che l'utente invii le modifiche dalla copia di lavoro all'archivio centrale del controllo del codice sorgente. In questo modo viene creata una nuova revisione del file disponibile per altri utenti. Questo processo è denominato checkin.  
  
 Checkout  
 Operazione di richiesta di una copia di lavoro dal repository, per informare il repository della finalità di modificarlo. Una copia di lavoro riflette lo stato del progetto nel momento in cui viene estratto.  
  
 Client  
 Programma che utilizza il sistema di controllo del codice sorgente. Ai fini di questa documentazione, si tratta dell'IDE di Visual Studio.  
  
 Commento  
 Messaggio che descrive le modifiche che un utente può alleghire a una revisione quando viene eseguita un'operazione del controllo del codice sorgente.  
  
 Conflitto  
 Una situazione in cui due utenti tentano di archiviare le modifiche nella stessa area dello stesso file. In genere, è necessario eseguire un'operazione di merge.  
  
 Directory  
 Una cartella locale sul lato client viene denominata directory. Si tratta della copia in cui un utente apporta effettivamente modifiche. Possono essere presenti numerose copie di lavoro di un determinato progetto. in genere, ogni sviluppatore ha la propria copia.  
  
 Recupero  
 Un'operazione Get porta aggiornata la copia di lavoro dell'utente con la copia del repository. A differenza di un checkout, viene eseguita un'operazione get quando l'utente richiede semplicemente la copia più recente, ma intende apportare modifiche.  
  
 Cronologia  
 Si tratta in genere di un riepilogo di tutte le estrazioni, archiviazioni, aggiornamenti, tag e versioni eseguite nel repository del controllo del codice sorgente.  
  
 IDE  
 In genere si riferisce all'ambiente di sviluppo integrato di Visual Studio. Tuttavia, può anche fare riferimento ad altri ambienti client che riconoscono l'API del plug-in del controllo del codice sorgente.  
  
 Unione  
 Processo durante il quale due o più file di codice sorgente vengono combinati per formare un nuovo file che incorpora tutte le funzionalità dei file precedenti. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano contemporaneamente sui file.  
  
 Project  
 Una cartella del controllo del codice sorgente viene spesso definita progetto. Non esiste alcuna relazione con progetti o soluzioni in Visual Studio.  
  
 Plug-in  
 DLL che fornisce la funzionalità del controllo del codice sorgente implementando l'API del plug-in del controllo del codice sorgente.  
  
 Archivio  
 La copia master in cui un sistema di controllo del codice sorgente archivia la cronologia delle revisioni completa di un progetto. Ogni progetto include esattamente un repository.  
  
 Revisione  
 Una modifica di cui è stato eseguito il commit nella cronologia di un file o di un set di file. Una revisione è uno snapshot in un progetto continuamente modificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
