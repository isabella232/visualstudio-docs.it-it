---
title: 'Procedura: Installare Visual Studio Tools per Office runtime redistributable'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205fb184997130423072d556a60e1323a99e6ad8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101457"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procedura: Installare Visual Studio Tools per Office runtime redistributable
  Visual Studio 2010 Tools per Office runtime deve essere installato in ogni computer che eseguono le soluzioni create con Microsoft Office developer tools in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Il runtime viene installato automaticamente all'installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di Microsoft Office. Per altre informazioni, vedere [Visual Studio Tools per scenari di installazione di Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 Attenersi alle seguenti istruzioni di installazione manuale, se si verificano le situazioni riportate di seguito:

- È necessario installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] su un server. Ad esempio, si desidera utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per gestire soluzioni a livello di documento su un server.

- È necessario installare il runtime in un computer su cui sono già installati tutti i prerequisiti delle soluzioni di Office.

    > [!NOTE]
    >  Per installare .NET Framework e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è necessario essere un amministratore del computer di sviluppo.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Per installare l'assembly nel runtime di Visual Studio Tools per Office

1. Installare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva.

    - Per scaricare il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], vedere [Microsoft.NET Framework 4 (programma di installazione Web)](http://go.microsoft.com/fwlink/?LinkId=178957).

    - Per scaricare il [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], vedere [Microsoft.NET Framework 4 Client Profile (programma di installazione Web)](http://go.microsoft.com/fwlink/?LinkId=178958).

    - Per scaricare il [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vedere [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).

2. Eseguire *vstor_redist.exe* per installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     È possibile scaricare questi file di installazione dal [Visual Studio 2010 Tools per Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). I prerequisiti per [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corrispondono a quelli per .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include i Language Pack. Se l'installazione di Windows è impostata su una lingua diversa dall'inglese, è possibile visualizzare i messaggi di runtime nella stessa lingua utilizzata da Windows. Analogamente, se gli utenti finali installano [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ed eseguono le soluzioni in versioni di Windows impostate su una lingua diversa dall'inglese, verranno visualizzati i messaggi di runtime nella stessa lingua di Windows. In alcuni casi, potrebbe essere necessario installare Language Pack aggiuntivi. Ad esempio, potrebbe essere necessario language pack aggiuntivi se la copia di Windows utilizza più di una impostazione della lingua, o si passa a un'altra lingua dopo che è già stato installato il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. È possibile trovare i language pack in [Microsoft Visual Studio 2010 Tools per Microsoft Office system (versione 4.0 runtime) language pack](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>Vedere anche
- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Procedura: Configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare l'assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gestire documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
