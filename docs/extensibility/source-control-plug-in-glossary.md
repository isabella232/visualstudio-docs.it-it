---
title: Glossario del plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699901"
---
# <a name="source-control-plug-in-glossary"></a>Glossario del plug-in del controllo del codice sorgente
I seguenti termini e definizioni utili riguardano la documentazione SDK del plug-in del controllo del codice sorgente.

## <a name="definitions"></a>Definizioni
 Checkin Quando un utente apporta modifiche a una copia di lavoro, un utente deve inviare le modifiche dalla copia di lavoro nel repository del controllo del codice sorgente centrale. In questo modo viene creata una nuova revisione del file disponibile per altri utenti. Questo processo è chiamato check-in.

 Estrazione L'atto di richiedere una copia di lavoro dal repository, informando il repository dell'intenzione di modificarla. Una copia di lavoro riflette lo stato del progetto al momento in cui è stato estratto.

 Client Un programma che utilizza il sistema di controllo del codice sorgente. Ai fini di questa documentazione, è l'IDE di Visual Studio.For the purpose of this documentation, it is the Visual Studio IDE.

 Commento Messaggio che descrive le modifiche che un utente può allegare a una revisione quando viene eseguita un'operazione del controllo del codice sorgente.

 Conflitto Una situazione in cui due utenti tentano di archiviare le modifiche alla stessa area dello stesso file. In genere, è necessario eseguire un'unione.

 Directory Una cartella locale sul lato client viene definita directory. Questa è la copia in cui un utente apporta effettivamente modifiche. Ci possono essere molte copie di lavoro di un determinato progetto; in genere ogni sviluppatore ha la propria copia.

 Get Un'operazione get aggiorna la copia di lavoro dell'utente con la copia del repository. A differenza di un checkout, un get viene eseguito quando l'utente ha semplicemente bisogno della copia più recente, ma intende non apportare modifiche.

 Cronologia Si tratta in genere di un riepilogo di tutte le estrazioni, archiviazioni, aggiornamenti, tag e versioni eseguite nel repository del controllo del codice sorgente.

 IDE Generally refers to the Visual Studio Integrated Development Environment. Tuttavia, potrebbe anche fare riferimento ad altri ambienti client che riconoscono l'API plug-in del controllo del codice sorgente.

 Unisci Il processo durante il quale due o più file di codice sorgente vengono combinati per formare un nuovo file che incorpora tutte le funzionalità dei file precedenti. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano sui file contemporaneamente.

 Progetto Una cartella del controllo del codice sorgente viene spesso definita progetto. Ciò non ha alcuna relazione con progetti o soluzioni in Visual Studio.This does not have any relationship with projects or solutions in Visual Studio.

 Plug-in UNA DLL che fornisce funzionalità di controllo del codice sorgente implementando l'API del plug-in del controllo del codice sorgente.

 Repository La copia master in cui un sistema di controllo del codice sorgente archivia la cronologia completa delle revisioni di un progetto. Ogni progetto ha esattamente un repository.

 Revisione Una modifica impegnata nella cronologia di un file o di un insieme di file. Una revisione è un'istantanea in un progetto in continua evoluzione.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
