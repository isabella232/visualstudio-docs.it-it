---
title: 'Procedura: Configurare un computer per sviluppare Office soluzioni'
description: Informazioni su come configurare un computer di sviluppo in modo da poter usare Microsoft Office strumenti di sviluppo in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d5868a8a7e8eca8bf75436eed3c2bd17c4238b29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026226"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procedura: Configurare un computer per sviluppare Office soluzioni
  Per configurare un computer di sviluppo in modo tale da poter utilizzare gli strumenti di sviluppo di Microsoft Office in Visual Studio, seguire le istruzioni in questo argomento. Per seguire la procedura, è necessario disporre dei privilegi amministrativi sul computer di sviluppo.

### <a name="to-configure-the-development-computer"></a>Per configurare il computer di sviluppo

1. Installare una versione di Visual Studio che includa gli strumenti di sviluppo di Office. Gli strumenti di sviluppo di Office vengono installati per impostazione predefinita. Se si personalizza l Visual Studio installazione selezionando le funzionalità da installare, **assicurarsi** Microsoft Office Strumenti di sviluppo durante l'installazione. Per altre informazioni sulle versioni di Visual Studio che includono gli strumenti di sviluppo Office, vedere Configurare un computer per sviluppare Office [soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Installare una versione di Office supportata dagli strumenti di sviluppo di Office in Visual Studio. Per altre informazioni, vedere [Configurare un computer per sviluppare Office soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Assicurarsi inoltre di installare gli assembly di interoperabilità primari per la versione di Office installata. Per impostazione predefinita, gli assembly di interoperabilità primari vengono installati con Office. Se si modifica Office configurazione, assicurarsi che la funzionalità Supporto programmabilità **.NET** sia selezionata per le applicazioni di destinazione.

3. Se si ha una versione inglese di Visual Studio ma si usano impostazioni non in lingua inglese per Windows, è possibile installare il language pack per visualizzare i messaggi nella stessa lingua del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows. Le versioni non in lingua inglese di Visual Studio installano automaticamente il language pack. Il language pack è disponibile [nell'Area download Microsoft.](https://www.microsoft.com/download/details.aspx?id=54246)

## <a name="see-also"></a>Vedi anche

- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Procedura: Installare il runtime Visual Studio Tools per Office ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Procedura: Installare Office assembly di interoperabilità primari](../vsto/how-to-install-office-primary-interop-assemblies.md)
