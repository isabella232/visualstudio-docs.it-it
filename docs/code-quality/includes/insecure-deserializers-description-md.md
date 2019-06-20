---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67254178"
---
Deserializers non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere i tipi imprevisti per l'inserimento di oggetti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro può, ad esempio, eseguire i comandi nel sistema operativo sottostante, comunichi sulla rete o eliminare file.