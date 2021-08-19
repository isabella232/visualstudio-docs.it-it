---
title: Destinazione Office app tramite assembly di interoperabilità primari
description: Informazioni su come usare Visual Studio destinazione a livello di codice Microsoft Office applicazioni tramite assembly di interoperabilità primari.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5172fb15b1a44961738627929ac5486302cc28d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099633"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Procedura: Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari
  Quando si crea un nuovo progetto di Office, in Visual Studio vengono aggiunti automaticamente riferimenti agli assembly di interoperabilità primari (PIA) di Microsoft Office necessari per la compilazione del progetto. È necessario aggiungere riferimenti agli altri assembly di interoperabilità primari (PIA) negli scenari seguenti:

- Si vuole usare funzionalità di altre applicazioni di Microsoft Office nel progetto, ad esempio, funzionalità di Microsoft Office Excel in un progetto per Microsoft Office Word.

- Si vuole automatizzare applicazioni di Microsoft Office prive di progetti dedicati in Visual Studio, ad esempio Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Per aggiungere un riferimento a un assembly di interoperabilità primario

1. Aprire il Office progetto e selezionare il nome del progetto in **Esplora soluzioni**.

2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

3. Nella scheda **Framework** selezionare l'elenco piasto desiderato nell'elenco **Nome** componente. Per altre informazioni sugli assembly di interoperabilità Microsoft Office primari, vedere Office [assembly di interoperabilità primari.](../vsto/office-primary-interop-assemblies.md)

     Se il progetto è destinato a o versioni successive, la proprietà Incorpora tipi di interoperabilità per il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] riferimento all'assembly  è impostata su **True** per impostazione predefinita. Usando questa impostazione, la soluzione non richiede l'assembly di interoperabilità primario (PIA) sui computer degli utenti finali. Per altre informazioni, vedere [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > Nei Office, aggiungere sempre riferimenti Office assembly di interoperabilità personali usando la  scheda **.NET** della finestra di dialogo Aggiungi riferimento anziché la **scheda COM.** Per altre informazioni, vedere Office [assembly di interoperabilità primari.](../vsto/office-primary-interop-assemblies.md)

4. Fare clic su **OK**.

     Il nome dell'assembly viene visualizzato nella **cartella Riferimenti** di **Esplora soluzioni**.

## <a name="see-also"></a>Vedi anche
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Procedura: Installare Office assembly di interoperabilità primari](../vsto/how-to-install-office-primary-interop-assemblies.md)
