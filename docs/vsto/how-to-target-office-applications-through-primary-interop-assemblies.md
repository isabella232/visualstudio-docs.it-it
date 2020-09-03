---
title: App di Office di destinazione tramite assembly di interoperabilità primari
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60e351a15af4994d2bf64a800e3019501cf0571d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545769"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari
  Quando si crea un nuovo progetto di Office, in Visual Studio vengono aggiunti automaticamente riferimenti agli assembly di interoperabilità primari (PIA) di Microsoft Office necessari per la compilazione del progetto. È necessario aggiungere riferimenti agli altri assembly di interoperabilità primari (PIA) negli scenari seguenti:

- Si vuole usare funzionalità di altre applicazioni di Microsoft Office nel progetto, ad esempio, funzionalità di Microsoft Office Excel in un progetto per Microsoft Office Word.

- Si vuole automatizzare applicazioni di Microsoft Office prive di progetti dedicati in Visual Studio, ad esempio Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Per aggiungere un riferimento a un assembly di interoperabilità primario

1. Aprire il progetto di Office e selezionare il nome del progetto in **Esplora soluzioni**.

2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

3. Nella scheda **Framework** selezionare l'assembly di interoperabilità primario desiderato nell'elenco **nome componente** . Per ulteriori informazioni sugli assembly di interoperabilità primari disponibili Microsoft Office, vedere [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

     Se il progetto è destinato [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a o versione successiva, la proprietà **Incorpora tipi di interoperabilità** per il riferimento all'assembly è impostata su **true** per impostazione predefinita. Usando questa impostazione, la soluzione non richiede l'assembly di interoperabilità primario (PIA) sui computer degli utenti finali. Per ulteriori informazioni, vedere [progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > Nei progetti di Office aggiungere sempre i riferimenti agli assembly di interoperabilità primari di Office usando la scheda **.NET** della finestra di dialogo **Aggiungi riferimento** anziché la scheda **com** . Per altre informazioni, vedere [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).

4. Fare clic su **OK**.

     Il nome dell'assembly viene visualizzato nella cartella **riferimenti** del **Esplora soluzioni**.

## <a name="see-also"></a>Vedere anche
- [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
