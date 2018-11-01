---
title: 'Procedura: configurare un computer per sviluppare soluzioni Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6a07545fb9a7ddb2fc70ba5053ad131d2e214636
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671313"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procedura: configurare un computer per sviluppare soluzioni Office
  Per configurare un computer di sviluppo in modo tale da poter utilizzare gli strumenti di sviluppo di Microsoft Office in Visual Studio, seguire le istruzioni in questo argomento. Per seguire la procedura, è necessario disporre dei privilegi amministrativi sul computer di sviluppo.  
  
### <a name="to-configure-the-development-computer"></a>Per configurare il computer di sviluppo  
  
1.  Installare una versione di Visual Studio che includa gli strumenti di sviluppo di Office. Gli strumenti di sviluppo di Office vengono installati per impostazione predefinita. Se si personalizza l'installazione di Visual Studio, selezionare le funzionalità da installare, verificare che **Microsoft Office Developer Tools** selezionata durante l'installazione. Per altre informazioni sulle versioni di Visual Studio che include Office developer tools, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installare una versione di Office supportata dagli strumenti di sviluppo di Office in Visual Studio. Per altre informazioni, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Assicurarsi inoltre di installare gli assembly di interoperabilità primari per la versione di Office installata. Per impostazione predefinita, gli assembly di interoperabilità primari vengono installati con Office. Se si modifica il programma di installazione di Office, assicurarsi che il **Supporto programmabilità .NET** funzione è selezionata per le applicazioni di destinazione.  
  
3.  Se si utilizza una versione inglese di Visual Studio ma usano le impostazioni di lingua diversa dall'inglese per Windows, è possibile installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] language pack in modo da vedere [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] messaggi nella stessa lingua di Windows. Le versioni non in lingua inglese di Visual Studio installano automaticamente il language pack. Il language pack è disponibile il [area download Microsoft](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Vedere anche  
 [Quali sono le novità nello sviluppo per Office](https://msdn.microsoft.com/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Procedura: installare Visual Studio Tools per Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Procedura: assembly di interoperabilità primari di installazione di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  