---
title: 'Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando la finestra di progettazione del pacchetto | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 654773f5a5e46960f8c015cc6f731e16332fcdd7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094320"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti
  Quando si crea una soluzione di SharePoint, Visual Studio aggiunge le funzionalità di SharePoint predefinito per il pacchetto della soluzione. Prima della distribuzione definitiva, è possibile aggiungere e rimuovere elementi di progetto SharePoint e funzionalità per modificare il pacchetto di SharePoint.

 In alternativa, è possibile usare Esplora pacchetti per aggiungere e rimuovere elementi di progetto SharePoint. È anche possibile visualizzare e modificare la gerarchia delle funzionalità che vengono inserite nel pacchetto (con estensione wsp) e gli elementi di progetto SharePoint. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto usando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Aggiungere funzionalità a un pacchetto di SharePoint
 È possibile utilizzare la finestra di progettazione di pacchetti per aggiungere funzionalità a un pacchetto di SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Per aggiungere funzionalità di SharePoint con la progettazione di pacchetti

1. Aprire il **Progettazione pacchetti**.

    Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Aggiungere una o più funzionalità di SharePoint mediante l'esecuzione di uno o più delle operazioni seguenti:

   1. Fare doppio clic su ogni elemento di **elementi nella soluzione** elenco che si desidera aggiungere.

   2. Scegliere un elemento che si desidera aggiungere e quindi scegliere il **Add** (>).

   3. Scegliere il **Aggiungi tutto** pulsante (>>) per aggiungere tutti gli elementi in una sola volta.

      Ad esempio, è possibile fare doppio clic su un elemento nel **elementi nella soluzione** per aggiungerlo all'elenco il **elementi nel pacchetto** elenco.

      Gli elementi di progetto SharePoint e le funzionalità vengono visualizzati nei **gli elementi nel pacchetto** elenco.

## <a name="remove-features-from-a-sharepoint-package"></a>Rimuovere funzionalità da un pacchetto di SharePoint
 Per rimuovere funzionalità da un pacchetto di SharePoint, è possibile utilizzare la finestra di progettazione del pacchetto.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Per rimuovere le funzionalità di SharePoint con la progettazione di pacchetti

1. Nel **gli elementi nel pacchetto** elenco, scegliere un elemento che si desidera rimuovere e quindi scegliere il **rimuovere** (<) pulsante oppure scegliere il **Rimuovi tutto** pulsante (<<) da rimuovere tutti gli elementi.

     Gli elementi di SharePoint vengono visualizzati nei **elementi nella soluzione** elenco.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Creare un pacchetto](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
