---
title: 'Procedura: Configurare un computer per sviluppare soluzioni Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1f87b9548aceab58e1a8e1c6178a1dca759c312
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052845"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procedura: Configurare un computer per sviluppare soluzioni Office
  Per configurare un computer di sviluppo in modo tale da poter utilizzare gli strumenti di sviluppo di Microsoft Office in Visual Studio, seguire le istruzioni in questo argomento. Per seguire la procedura, è necessario disporre dei privilegi amministrativi sul computer di sviluppo.

### <a name="to-configure-the-development-computer"></a>Per configurare il computer di sviluppo

1. Installare una versione di Visual Studio che includa gli strumenti di sviluppo di Office. Gli strumenti di sviluppo di Office vengono installati per impostazione predefinita. Se si personalizza l'installazione di Visual Studio, selezionare le funzionalità da installare, verificare che **Microsoft Office Developer Tools** selezionata durante l'installazione. Per altre informazioni sulle versioni di Visual Studio che include Office developer tools, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Installare una versione di Office supportata dagli strumenti di sviluppo di Office in Visual Studio. Per altre informazioni, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Assicurarsi inoltre di installare gli assembly di interoperabilità primari per la versione di Office installata. Per impostazione predefinita, gli assembly di interoperabilità primari vengono installati con Office. Se si modifica il programma di installazione di Office, assicurarsi che il **Supporto programmabilità .NET** funzione è selezionata per le applicazioni di destinazione.

3. Se si utilizza una versione inglese di Visual Studio ma usano le impostazioni di lingua diversa dall'inglese per Windows, è possibile installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] language pack in modo da vedere [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] messaggi nella stessa lingua di Windows. Le versioni non in lingua inglese di Visual Studio installano automaticamente il language pack. Il language pack è disponibile il [area download Microsoft](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>Vedere anche

- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procedura: Installare Visual Studio Tools per Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Procedura: Installare l'assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
