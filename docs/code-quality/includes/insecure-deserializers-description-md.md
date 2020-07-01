---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147090"
---
I deserializzatori non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere tipi imprevisti per inserire oggetti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro potrebbe, ad esempio, eseguire comandi sul sistema operativo sottostante, comunicare in rete o eliminare file.