---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65840905"
---
Deserializers non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere i tipi imprevisti per l'inserimento di oggetti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro può, ad esempio, eseguire i comandi nel sistema operativo sottostante, comunichi sulla rete o eliminare file.