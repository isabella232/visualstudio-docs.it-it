---
title: Visual Studio Tools per Office scenari di installazione di runtime
description: Informazioni su come installare gli strumenti Visual Studio 2010 per Office runtime. Questo articolo descrive tre scenari di installazione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 110e78b404ef5d25264a0e168bf9b6de5cad5d3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082686"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools per Office scenari di installazione di runtime

  È possibile installare gli strumenti Visual Studio 2010 per Office runtime in tre modi:

- Quando si installa Visual Studio.

- Quando si installa Microsoft Office.

- Quando si installa la versione Visual Studio 2010 Tools per Office runtime ridistribuibile.

  I componenti runtime vengono installati in base alla configurazione del computer e allo scenario di installazione.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componenti di runtime installati in ogni scenario di installazione

 Il runtime di Visual Studio 2010 Tools per Office ha tre componenti: il caricatore della soluzione Office, le estensioni Office per .NET Framework 3.5 e le estensioni Office per o versioni [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] successive. Quando si installa il runtime, il caricatore di soluzioni Office viene sempre installato. L'installazione delle estensioni di Office per .NET Framework dipende dalla configurazione del computer e dallo scenario di installazione. Se una delle estensioni di Office non può essere installata quando il runtime viene installato per la prima volta, il runtime installerà automaticamente le estensioni di Office mancanti in un secondo momento, quando determinati requisiti saranno soddisfatti. Questa funzionalità del runtime è denominata *installazione su richiesta.*

 Nella tabella seguente vengono illustrati i componenti runtime installati per impostazione predefinita in ogni scenario di installazione del runtime. Ulteriori informazioni su ogni scenario verranno visualizzate in un secondo momento.

|Scenario di installazione del runtime|Caricatore di soluzioni di Office|Estensioni di Office per .NET Framework 3.5|Estensioni di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Estensioni di Office per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] e versione successiva|Sì|Sì, se è già installata .NET Framework 3.5.|Sì|Sì|
|Con [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sì|Sì, se è già installata .NET Framework 3.5.|No|No|
|Con Office 2010 Service Pack 1 (SP1) o versione successiva|Sì|Sì, se è già installata .NET Framework 3.5.|Sì, se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] è già installato.|No|
|Con Office 2013 e versione più recente|Sì|Sì, se è già installata .NET Framework 3.5|Sì, se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] è già installato.|Sì, se [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] è già installato.|
|Con runtime ridistribuibile|Sì|Sì, se è già installata .NET Framework 3.5|Sì, se [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] è già installato.|Sì, se [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] è già installato.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Installare il runtime con Visual Studio o il Microsoft Office Strumenti di sviluppo per Visual Studio

 Quando si installano gli strumenti di sviluppo di Office in Visual Studio, le estensioni di Office per [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] vengono sempre installate nel computer di sviluppo. Le estensioni di Office per .NET Framework 3.5 vengono installate solo se .NET Framework 3.5. è già presente nel computer di sviluppo. Se si installa .NET Framework 3.5 dopo l'installazione di [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], tramite il runtime vengono installate automaticamente le estensioni di Office per .NET Framework 3.5 la prima volta che si crea un progetto Office destinato a .NET Framework 3.5.

> [!WARNING]
> Non è possibile creare un progetto Office destinato a .NET Framework 3.5 utilizzando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o versione successiva.

 Per altre informazioni su come installare gli strumenti di sviluppo Office, vedere [Procedura: Configurare](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)un computer per sviluppare Office applicazioni .

### <a name="install-the-runtime-with-office"></a>Installare il runtime con Office

 Quando si installa Office, le estensioni di Office per .NET Framework 3.5 vengono installate solo se .NET Framework 3.5. è già presente nel computer di sviluppo. Se si installa .NET Framework 3.5 dopo Office, il runtime installerà automaticamente le estensioni di Office per .NET Framework 3.5 la prima volta che un'applicazione Office prova a caricare una soluzione destinata a .NET Framework 3.5.

 Le Office per o versioni successive vengono installate anche con Office se le versioni corrispondenti del .NET Framework sono già [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] presenti nel computer.

 Per assicurarsi che gli utenti siano in grado di usare l'applicazione con le estensioni necessarie, includere la versione più recente di Visual Studio 2010 Tools for Office Runtime Redistributable come prerequisito per la soluzione. Per altre informazioni sui prerequisiti, vedere l'Office [della soluzione per la distribuzione](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Installare il runtime usando il runtime ridistribuibile

 È possibile installare il runtime eseguendo manualmente gli strumenti di Visual Studio 2010 per Office Runtime ridistribuibili o includendo il ridistribuibile come prerequisito quando si distribuisce una soluzione Office.

 Quando si installa il runtime usando gli strumenti di Visual Studio 2010 per Office runtime ridistribuibili, le estensioni Office per .NET Framework 3.5 e le estensioni Office per o versioni successive vengono installate se le versioni corrispondenti del .NET Framework sono già presenti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nel computer. Se nel computer manca una di queste versioni di .NET Framework quando è installato il runtime, le estensioni di Office per la versione mancante di .NET Framework al momento non vengono installate. Se si installa la versione mancante di .NET Framework in un secondo momento, il runtime installerà automaticamente le estensioni di Office corrispondenti alla successiva installazione (se il runtime è stato installato con una soluzione che è stata distribuita tramite ClickOnce) o al successivo caricamento (se il runtime è stato installato con una soluzione che è stata distribuita tramite Windows Installer) di una soluzione che richiede le estensioni.

 Per altre informazioni sull'inclusione dei prerequisiti in una soluzione ClickOnce, vedere [Procedura: Installare](/previous-versions/bb608608(v=vs.110))i prerequisiti nei computer degli utenti finali per eseguire Office soluzioni . Per altre informazioni su come installare manualmente il runtime dal pacchetto ridistribuibile, vedere Procedura: Installare Visual Studio Tools per Office [runtime ridistribuibile.](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

## <a name="see-also"></a>Vedi anche

- [Visual Studio Tools per Office di runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Assembly nel runtime Visual Studio Tools per Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
