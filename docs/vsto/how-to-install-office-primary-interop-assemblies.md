---
title: "Procedura: Installare l'assembly di interoperabilità primari di Office"
ms.date: 02/02/2017
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
ms.openlocfilehash: 2ddba23ecb6007ff3b678932b118208742d1f0d4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109504"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procedura: Installare l'assembly di interoperabilità primari di Office
  Quando si installa Office, installare gli assembly di interoperabilità primari (PIA) di Microsoft Office.

## <a name="to-install-the-pias-when-you-install-office"></a>Per installare gli assembly di interoperabilità primari durante l'installazione di Office

1. Assicurarsi di avere una versione di.NET Framework che non sia precedente alla versione 2.0.

2. Installare Microsoft Office e assicurarsi che il **Supporto programmabilità .NET** funzione è selezionata per le applicazioni che si desidera estendere (questa funzionalità è inclusa nell'installazione predefinita).

    > [!WARNING]
    >  Per impostazione predefinita, assembly di interoperabilità primari vengono incorporati nella soluzione durante la compilazione in modo da non dover distribuire assembly di interoperabilità primari agli utenti come prerequisito per l'uso del componente aggiuntivo VSTO o della personalizzazione.

## <a name="see-also"></a>Vedere anche
- [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Procedura: Configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare Visual Studio Tools per Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
