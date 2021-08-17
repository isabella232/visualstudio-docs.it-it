---
title: 'Procedura: Installare Office assembly di interoperabilità primari'
description: Informazioni su come installare Microsoft Office assembly di interoperabilità primari (PIA) quando si installa Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d0a5ffcf0a7c9c3533eee85953b26d9341a537a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100023"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procedura: Installare Office assembly di interoperabilità primari
  Quando si installa Office, installare gli assembly di interoperabilità primari (PIA) di Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Per installare gli assembly di interoperabilità primari durante l'installazione di Office

1. Assicurarsi di avere una versione di.NET Framework che non sia precedente alla versione 2.0.

2. Installare Microsoft Office e assicurarsi che la funzionalità Supporto programmabilità **.NET** sia selezionata per le applicazioni da estendere (questa funzionalità è inclusa nell'installazione predefinita).

    > [!WARNING]
    > Per impostazione predefinita, gli assembly di interoperabilità personali sono incorporati nella soluzione quando la si compila, quindi non è necessario distribuire gli assembly di interoperabilità personali agli utenti come prerequisito per l'uso del componente aggiuntivo o della personalizzazione VSTO.

## <a name="see-also"></a>Vedi anche
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Procedura: Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Procedura: Configurare un computer per sviluppare Office soluzioni](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: Installare il runtime Visual Studio Tools per Office ridistribuibile](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
