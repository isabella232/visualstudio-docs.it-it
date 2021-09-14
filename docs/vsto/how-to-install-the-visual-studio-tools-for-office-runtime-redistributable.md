---
title: 'Procedura: Installare il runtime Visual Studio Tools per Office ridistribuibile'
description: Informazioni su come installare gli strumenti Microsoft Visual Studio 2010 per Office runtime ridistribuibile.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c9c74cd354f89725352c5c8b22557956fcd9624c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634043"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procedura: Installare il runtime Visual Studio Tools per Office ridistribuibile
  Il runtime di Visual Studio 2010 Tools per Office deve essere installato in ogni computer che esegue soluzioni create usando gli strumenti di sviluppo Microsoft Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Il runtime viene installato automaticamente all'installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di Microsoft Office. Per altre informazioni, vedere scenari [Visual Studio Tools per Office di installazione di runtime.](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)

[!include[Add-ins note](includes/addinsnote.md)]

 Attenersi alle seguenti istruzioni di installazione manuale, se si verificano le situazioni riportate di seguito:

- È necessario installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] su un server. Ad esempio, si desidera utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per gestire soluzioni a livello di documento su un server.

- È necessario installare il runtime in un computer su cui sono già installati tutti i prerequisiti delle soluzioni di Office.

    > [!NOTE]
    > Per installare .NET Framework e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è necessario essere un amministratore del computer di sviluppo.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Per installare l'assembly nel runtime di Visual Studio Tools per Office

1. Installare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva.

    - Per scaricare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , vedere Microsoft .NET Framework [4 (Programma di installazione Web).](https://www.microsoft.com/download/details.aspx?id=17851)

    - Per scaricare [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , vedere Microsoft .NET Framework [4 Client Profile (Programma di installazione Web).](https://www.microsoft.com/download/details.aspx?id=17113)

    - Per scaricare [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , vedere Microsoft .NET Framework [4.5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Eseguire *vstor_redist.exe* per installare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     È possibile scaricare questi file di installazione [da Visual Studio 2010 Tools for Office runtime](https://www.microsoft.com/download/details.aspx?id=56961). I prerequisiti per [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corrispondono a quelli per .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include i Language Pack. Se l'installazione di Windows è impostata su una lingua diversa dall'inglese, è possibile visualizzare i messaggi di runtime nella stessa lingua utilizzata da Windows. Analogamente, se gli utenti finali installano [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ed eseguono le soluzioni in versioni di Windows impostate su una lingua diversa dall'inglese, verranno visualizzati i messaggi di runtime nella stessa lingua di Windows. In alcuni casi, potrebbe essere necessario installare Language Pack aggiuntivi. Ad esempio, potrebbero essere necessari Language Pack aggiuntivi se la copia di Windows usa più di un'impostazione di lingua o se si passa a un'altra lingua dopo aver già installato [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . I Language Pack sono disponibili [Microsoft Visual Studio 2010 Tools for the Microsoft Office System (version 4.0 runtime) language pack](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Vedi anche
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurare un computer per sviluppare Office soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Procedura: Configurare un computer per sviluppare Office soluzioni](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare Office assembly di interoperabilità primari](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
