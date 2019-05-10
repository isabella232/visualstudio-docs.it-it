---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459364"
---
Deserializers non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere i tipi imprevisti per l'inserimento di oggetti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro può, ad esempio, eseguire i comandi nel sistema operativo sottostante, comunichi sulla rete o eliminare file.