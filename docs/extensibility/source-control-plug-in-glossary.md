---
title: Glossario del plug-in del controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0df624a27513fa0eb18b2643bb7c680d71d94c0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722361"
---
# <a name="source-control-plug-in-glossary"></a>Glossario del plug-in del controllo del codice sorgente
I seguenti termini utili e le definizioni sono relativi alla documentazione SDK dei plug-in controllo di origine.

## <a name="definitions"></a>Definizioni
 Check-in quando un utente apporta modifiche a una copia di lavoro, un utente deve inviare le modifiche apportate dalla copia di lavoro nel repository di controllo di origine centrale. In questo modo viene creata una nuova revisione del file che è disponibile ad altri utenti. Questo processo è denominato archiviazione.

 Estrarre l'atto di richiedere una copia di lavoro dal repository, che informa l'archivio di funzione dell'intenzione di modificarlo. Una copia di lavoro riflette lo stato del progetto al momento che è estratto.

 Programma del client che usa il sistema di controllo del codice sorgente. Ai fini di questa documentazione è l'IDE di Visual Studio.

 Messaggio di commento che descrive le modifiche che è possibile collegare a una revisione quando viene eseguita un'operazione di controllo del codice sorgente.

 Situazione di conflitto quando due utenti tentano di verificare modifica alla stessa area dello stesso file. In genere, è necessario eseguire un'operazione di merge.

 Cartella locale della directory A lato client si intende una directory. Si tratta della copia in cui viene effettivamente modificato. Possono essere presenti molte copie di lavoro di un determinato progetto; in genere ogni sviluppatore ha la propria copia.

 Operazione get di Get A porta copia lavoro dell'utente aggiornata con la copia del repository. A differenza di un checkpoint, viene eseguita un'operazione get quando l'utente richiede l'ultima copia semplicemente ma intende senza apportare alcuna modifica.

 Cronologia in genere è un riepilogo di tutte le estrazioni, archiviazioni, aggiornamenti, i tag e versioni richiede solo pochi repository del controllo del codice sorgente.

 IDE a livello generale si intende l'ambiente di sviluppo integrato di Visual Studio. Tuttavia, potrebbe inoltre fare riferimento ad altri ambienti client che riconosce l'API dei plug-in del controllo origine.

 Unire il processo durante la quale origine due o più file di codice vengono combinati per formare un nuovo file che incorpora tutte le funzionalità del file precedente. Questo concetto è fondamentale nel controllo della versione in cui due o più sviluppatori lavorano sui file contemporaneamente.

 Cartella del codice sorgente di progetto è noto anche come un progetto. Questo non hanno alcuna relazione con i progetti o soluzioni in Visual Studio.

 Plug-in una DLL che fornisce la funzionalità di controllo sorgente implementando l'API dei plug-in del controllo origine.

 Repository della copia master in cui un controllo del codice sorgente archivia la cronologia delle revisioni completo di un progetto. Ogni progetto ha un solo repository.

 Revisione a eseguito il commit delle modifiche nella cronologia di un file o set di file. Una revisione è uno snapshot in un progetto in continua evoluzione.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)