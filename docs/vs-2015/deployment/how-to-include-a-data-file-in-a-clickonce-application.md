---
title: "Procedura: includere un File di dati in un'applicazione ClickOnce | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee465b3b4524b4f5c530369722f8bdaf36b85227
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540448"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procedura: includere un file di dati in un'applicazione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: includere un File di dati in un'applicazione ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).  
  
Ogni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installata è assegnata una directory di dati sul disco locale del computer di destinazione in cui l'applicazione può gestire i propri dati. File di dati possono includere file di qualsiasi tipo: file di testo, file XML o anche i file di Microsoft Access (mdb). Le procedure seguenti illustrano come aggiungere un file di dati di qualsiasi tipo nel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Per includere un file di dati usando Mage.exe  
  
1.  Aggiungere il file di dati alla directory dell'applicazione con il resto del file dell'applicazione.  
  
     In genere, la directory dell'applicazione è una directory contrassegnata con la versione corrente di distribuzione, ad esempio, v1.0.0.0.  
  
2.  Aggiornare il manifesto dell'applicazione all'elenco di file di dati.  
  
     **Mage -u v1.0.0.0\Application.manifest - FromDirectory v1.0.0.0**  
  
     Per eseguire questa attività verrà ricreato l'elenco dei file nel manifesto dell'applicazione e genera anche automaticamente le firme hash.  
  
3.  Aprire il manifesto dell'applicazione nell'editor XML di testo preferito o e trovare il `file` (elemento) per il file aggiunto di recente.  
  
     Se è stato aggiunto un file XML denominato `Data.xml`, il file avrà un aspetto simile al seguente esempio di codice.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Aggiungere l'attributo `type` a questo elemento, quindi assegnare il valore `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Firmare nuovamente il manifesto dell'applicazione usando la coppia di chiavi o un certificato e quindi firmare nuovamente il manifesto della distribuzione.  
  
     È necessario firmare nuovamente il manifesto di distribuzione perché il relativo hash del manifesto dell'applicazione è stata modificata.  
  
     **app -s Mage manifesto - cf cert_file - pwd password**  
  
     **Mage -u - appm manifesto dell'app del manifesto**  
  
     **manifesto della distribuzione -s di Mage cf - certfile - pwd password**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Per includere un file di dati usando MageUI.exe  
  
1.  Aggiungere il file di dati alla directory dell'applicazione con il resto del file dell'applicazione.  
  
2.  In genere, la directory dell'applicazione è una directory contrassegnata con la versione corrente di distribuzione, ad esempio, v1.0.0.0.  
  
3.  Nel **File** menu, fare clic su **aprire** per aprire il manifesto dell'applicazione.  
  
4.  Selezionare il **file** scheda.  
  
5.  Nella casella di testo nella parte superiore della scheda, immettere la directory che contiene i file dell'applicazione e quindi fare clic su **Popola**.  
  
     Il file di dati verrà visualizzato nella griglia.  
  
6.  Impostare il **tipo di File** valore del file di dati **dati**.  
  
7.  Salvare il manifesto dell'applicazione e quindi firmare nuovamente il file.  
  
     MageUI.exe chiederà di firmare nuovamente il file.  
  
8.  Firmare nuovamente il manifesto di distribuzione  
  
     È necessario firmare nuovamente il manifesto di distribuzione perché il relativo hash del manifesto dell'applicazione è stata modificata.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



