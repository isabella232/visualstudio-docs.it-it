---
title: 'Procedura: configurare un computer per sviluppare soluzioni Office'
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
ms.openlocfilehash: eb29dc4151bc457eb60ce836986817bc1b0137c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985958"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procedura: configurare un computer per sviluppare soluzioni Office
  Per configurare un computer di sviluppo in modo tale da poter utilizzare gli strumenti di sviluppo di Microsoft Office in Visual Studio, seguire le istruzioni in questo argomento. Per seguire la procedura, è necessario disporre dei privilegi amministrativi sul computer di sviluppo.

### <a name="to-configure-the-development-computer"></a>Per configurare il computer di sviluppo

1. Installare una versione di Visual Studio che includa gli strumenti di sviluppo di Office. Gli strumenti di sviluppo di Office vengono installati per impostazione predefinita. Se si Personalizza l'installazione di Visual Studio selezionando le funzionalità da installare, assicurarsi che **Microsoft Office strumenti di sviluppo** sia selezionato durante l'installazione. Per altre informazioni sulle versioni di Visual Studio che includono gli strumenti di sviluppo di Office, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Installare una versione di Office supportata dagli strumenti di sviluppo di Office in Visual Studio. Per altre informazioni, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Assicurarsi inoltre di installare gli assembly di interoperabilità primari per la versione di Office installata. Per impostazione predefinita, gli assembly di interoperabilità primari vengono installati con Office. Se si modifica il programma di installazione di Office, assicurarsi che sia selezionata la funzionalità **Supporto programmabilità .NET** per le applicazioni di destinazione.

3. Se si dispone di una versione in lingua inglese di Visual Studio, ma si utilizzano le impostazioni non in lingua inglese per Windows, è possibile installare il Language Pack [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per visualizzare i messaggi di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nella stessa lingua di Windows. Le versioni non in lingua inglese di Visual Studio installano automaticamente il language pack. Il Language Pack è disponibile nell' [area download Microsoft](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Vedere anche

- [Introduzione &#40;allo sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procedura: installare la Strumenti di Visual Studio per Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
