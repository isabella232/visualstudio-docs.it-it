---
title: Glossario del plug-in del controllo del codice sorgente | Microsoft Docs
description: Questo articolo include termini e definizioni utili relativi alla documentazione dell'SDK del plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05b215de4191362a539d3b03ac858da6bb7ee292
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899524"
---
# <a name="source-control-plug-in-glossary"></a>Glossario del plug-in del controllo del codice sorgente
I termini e le definizioni utili seguenti riguardano la documentazione dell'SDK del plug-in del controllo del codice sorgente.

## <a name="definitions"></a>Definizioni
 Checkin Quando un utente apporta modifiche a una copia di lavoro, deve inviare le modifiche dalla copia di lavoro al repository centrale del controllo del codice sorgente. Verrà creata una nuova revisione del file disponibile per altri utenti. Questo processo è detto checkin.

 Checkout L'atto di richiedere una copia di lavoro dal repository, informando il repository della finalità di modificarla. Una copia di lavoro riflette lo stato del progetto al momento dell'estrazione.

 Client Programma che usa il sistema di controllo del codice sorgente. Ai fini di questa documentazione, è l'IDE Visual Studio.

 Commento Messaggio che descrive le modifiche che un utente può allegare a una revisione quando viene eseguita un'operazione di controllo del codice sorgente.

 Conflitto Una situazione in cui due utenti tentano di archiviare le modifiche nella stessa area dello stesso file. In genere, è necessario eseguire un'unione.

 Directory Una cartella locale sul lato client viene definita directory. Si tratta della copia in cui un utente apporta effettivamente modifiche. Possono essere presenti molte copie di lavoro di un determinato progetto. in genere ogni sviluppatore ha la propria copia.

 Get A get operation (Ottieni un'operazione get) rende aggiornata la copia di lavoro dell'utente con la copia del repository. A differenza di un'estrazione, un'operazione get viene eseguita quando l'utente ha semplicemente bisogno della copia più recente, ma non intende apportare modifiche.

 Cronologia È in genere un riepilogo di tutte le estrazioni, le archiviazioni, gli aggiornamenti, i tag e le versioni eseguite nel repository del controllo del codice sorgente.

 L'IDE si riferisce in genere Visual Studio ambiente di sviluppo integrato. Tuttavia, potrebbe anche fare riferimento ad altri ambienti client che riconoscono l'API plug-in del controllo del codice sorgente.

 Merge Il processo durante il quale due o più file di codice sorgente vengono combinati per formare un nuovo file che incorpora tutte le funzionalità dei file precedenti. Questo concetto è essenziale nel controllo della versione in cui due o più sviluppatori lavorano contemporaneamente sui file.

 Progetto Una cartella del controllo del codice sorgente viene spesso definita progetto. Questa operazione non ha alcuna relazione con progetti o soluzioni in Visual Studio.

 Plug-in Dll che fornisce funzionalità di controllo del codice sorgente implementando l'API plug-in del controllo del codice sorgente.

 Repository Copia master in cui un sistema di controllo del codice sorgente archivia la cronologia di revisione completa di un progetto. Ogni progetto ha esattamente un repository.

 Revisione Modifica di cui è stato eseguito il commit nella cronologia di un file o di un set di file. Una revisione è uno snapshot di un progetto in continua evoluzione.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
