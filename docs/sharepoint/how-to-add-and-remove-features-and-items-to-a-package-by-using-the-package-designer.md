---
title: 'Progettazione pacchetti: aggiungere & rimuovere funzionalità ed elementi nel pacchetto'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 4dfbda711c42e475af5f17c8799e53b13e26611a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014614"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti
  Quando si crea una soluzione di SharePoint, Visual Studio aggiunge le funzionalità predefinite di SharePoint al pacchetto nella soluzione. Prima della distribuzione finale, è possibile aggiungere e rimuovere le funzionalità e gli elementi del progetto SharePoint per modificare il pacchetto di SharePoint.

 In alternativa, è possibile utilizzare Esplora pacchetti per aggiungere e rimuovere gli elementi del progetto SharePoint. È inoltre possibile visualizzare e modificare la gerarchia degli elementi e delle funzionalità del progetto SharePoint inseriti nel pacchetto (con estensione wsp). Per altre informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto con Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Aggiungere funzionalità a un pacchetto di SharePoint
 È possibile utilizzare Progettazione pacchetti per aggiungere funzionalità a un pacchetto di SharePoint.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Per aggiungere funzionalità di SharePoint con progettazione pacchetti

1. Aprire **Progettazione pacchetti**.

    Per ulteriori informazioni, vedere [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Aggiungere una o più funzionalità di SharePoint eseguendo uno o più dei passaggi seguenti:

   1. Fare doppio clic su ogni elemento negli **elementi nell'** elenco della soluzione che si desidera aggiungere.

   2. Scegliere un elemento che si desidera aggiungere, quindi scegliere il pulsante **Aggiungi** (>).

   3. Scegliere il pulsante **Aggiungi tutto** (>>) per aggiungere tutti gli elementi contemporaneamente.

      Ad esempio, è possibile fare doppio clic su un elemento negli **elementi** dell'elenco soluzione per aggiungerlo agli **elementi nell'** elenco dei pacchetti.

      Gli elementi e le funzionalità del progetto SharePoint vengono visualizzati negli **elementi nell'** elenco dei pacchetti.

## <a name="remove-features-from-a-sharepoint-package"></a>Rimuovere funzionalità da un pacchetto di SharePoint
 È possibile utilizzare Progettazione pacchetti per rimuovere le funzionalità di in un pacchetto di SharePoint.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Per rimuovere le funzionalità di SharePoint con progettazione pacchetti

1. In **elementi nell'elenco pacchetto** scegliere un elemento che si desidera rimuovere, quindi scegliere il pulsante **Rimuovi** (<) oppure scegliere il pulsante **Rimuovi tutto** (<<) per rimuovere tutti gli elementi.

     Gli elementi di SharePoint vengono visualizzati negli **elementi nell'** elenco della soluzione.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: creazione di un pacchetto](https://msdn.microsoft.com/b24be45c-e91d-49bb-afb0-7b265404214b)
