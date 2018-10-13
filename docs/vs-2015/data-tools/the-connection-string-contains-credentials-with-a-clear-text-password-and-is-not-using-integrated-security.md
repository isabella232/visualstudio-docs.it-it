---
title: La stringa di connessione contiene credenziali con una password in testo non crittografato e non usa la sicurezza integrata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1ec13cab1b8c41225cb1934740b8dd3e7f59ac0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230875"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Salvare la stringa di connessione nel file DBML corrente e i file di configurazione dell'applicazione con queste informazioni riservate?  Fare clic su No per salvare la stringa di connessione senza le informazioni riservate.  
  
 Quando si usano connessioni dati in cui sono contenute informazioni riservate, ad esempio le password incluse nella stringa di connessione, è possibile salvare la stringa di connessione nel file DBML di un progetto e il file di configurazione dell'applicazione con o senza le informazioni riservate.  
  
> [!WARNING]
>  Impostare in modo esplicito il **connessione** delle proprietà **le impostazioni dell'applicazione** proprietà **False** aggiungerà la password per il file DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione con le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Scegliere **Sì**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione e include le informazioni riservate in testo normale. Il file DBML non contiene le informazioni riservate.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione senza le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Fare clic su **No**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione, ma non viene inclusa la password.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

