---
title: 'Procedura: Installare gli assembly di interoperabilità primari di Office'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551802"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procedura: Installare gli assembly di interoperabilità primari di Office
  Quando si installa Office, installare gli assembly di interoperabilità primari (PIA) di Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Per installare gli assembly di interoperabilità primari durante l'installazione di Office

1. Assicurarsi di avere una versione di.NET Framework che non sia precedente alla versione 2.0.

2. Installare Microsoft Office e verificare che sia selezionata la funzionalità **Supporto programmabilità .NET** per le applicazioni che si desidera estendere. questa funzionalità è inclusa nell'installazione predefinita.

    > [!WARNING]
    > Per impostazione predefinita, gli assembly di interoperabilità primari sono incorporati nella soluzione durante la compilazione, in modo da non dover distribuire gli assembly di interoperabilità primari agli utenti come prerequisito per l'uso del componente aggiuntivo o della personalizzazione VSTO.

## <a name="see-also"></a>Vedere anche
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Procedura: Applicazioni di Office di destinazione tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Procedura: Configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare la Strumenti di Visual Studio per Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Panoramica &#40;dello sviluppo di soluzioni Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Introduzione &#40;allo sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
