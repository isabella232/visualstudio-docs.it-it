---
title: Glossario del plug-in del controllo del codice sorgente | Microsoft Docs
description: Questo articolo include termini e definizioni utili riguardanti la documentazione dell'SDK del plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6aaa8a1d88b946235863776c11fd805fecb0fd89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902885"
---
# <a name="source-control-plug-in-glossary"></a>Glossario del plug-in del controllo del codice sorgente
I termini e le definizioni utili seguenti riguardano la documentazione dell'SDK del plug-in del controllo del codice sorgente.

## <a name="definitions"></a>Definizioni
 Archiviazione quando un utente apporta modifiche a una copia di lavoro, è necessario che l'utente invii le modifiche dalla copia di lavoro all'archivio centrale del controllo del codice sorgente. In questo modo viene creata una nuova revisione del file disponibile per altri utenti. Questo processo è denominato checkin.

 Estrae l'azione di richiesta di una copia di lavoro dal repository, per informare il repository della finalità di modificarlo. Una copia di lavoro riflette lo stato del progetto nel momento in cui viene estratto.

 Client un programma che utilizza il sistema di controllo del codice sorgente. Ai fini di questa documentazione, si tratta dell'IDE di Visual Studio.

 Commentare un messaggio che descrive le modifiche che un utente può alleghire a una revisione quando viene eseguita un'operazione del controllo del codice sorgente.

 Conflitto tra le situazioni in cui due utenti tentano di archiviare le modifiche nella stessa area dello stesso file. In genere, è necessario eseguire un'operazione di merge.

 Directory una cartella locale sul lato client viene denominata directory. Si tratta della copia in cui un utente apporta effettivamente modifiche. Possono essere presenti numerose copie di lavoro di un determinato progetto. in genere, ogni sviluppatore ha la propria copia.

 Un'operazione Get consente di portare la copia di lavoro dell'utente aggiornata con la copia del repository. A differenza di un checkout, viene eseguita un'operazione get quando l'utente richiede semplicemente la copia più recente, ma intende apportare modifiche.

 Cronologia. si tratta in genere di un riepilogo di tutte le estrazioni, archiviazioni, aggiornamenti, tag e versioni eseguite nel repository del controllo del codice sorgente.

 L'IDE si riferisce in genere all'ambiente di sviluppo integrato di Visual Studio. Tuttavia, può anche fare riferimento ad altri ambienti client che riconoscono l'API del plug-in del controllo del codice sorgente.

 Unire il processo durante il quale due o più file di codice sorgente vengono combinati per formare un nuovo file che incorpora tutte le funzionalità dei file precedenti. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano contemporaneamente sui file.

 Progetto una cartella del controllo del codice sorgente è spesso definita progetto. Non esiste alcuna relazione con progetti o soluzioni in Visual Studio.

 Plug-in di una DLL che fornisce funzionalità di controllo del codice sorgente implementando l'API del plug-in del controllo del codice sorgente.

 Repository della copia master in cui un sistema di controllo del codice sorgente archivia la cronologia delle revisioni completa di un progetto. Ogni progetto include esattamente un repository.

 Revisione di una modifica di cui è stato eseguito il commit nella cronologia di un file o di un set di file. Una revisione è uno snapshot in un progetto continuamente modificato.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
