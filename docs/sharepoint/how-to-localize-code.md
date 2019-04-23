---
title: 'Procedura: Localizzare il codice | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbcf07b462e280f522741b8329d34c2907f5b454
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066286"
---
# <a name="how-to-localize-code"></a>Procedura: Localizzare il codice
  Codice non localizzato Usa i valori di stringa hardcoded. Per localizzare le stringhe di codice, sostituirli con chiamate a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, ovvero un metodo che fa riferimento a risorse localizzate.

## <a name="localize-code"></a>Localizzare il codice

#### <a name="to-localize-code"></a>Per localizzare il codice

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per un elemento di progetto e quindi scegliere **Add** > **modulo**.

     Scegliere il **File di risorse** modello.

    > [!NOTE]
    >  Assicurarsi di aggiungere il file di risorse a un elemento del progetto SharePoint in modo che la proprietà del tipo di distribuzione è disponibile. Questa proprietà è necessaria più avanti in questa procedura.

2. Assegnare un nome di propria scelta con i file di risorse di lingua predefinito un *resx* estensione, ad esempio *MyAppResources*.

3. Ripetere i passaggi 1 e 2 per aggiungere file di risorse separati all'elemento di progetto SharePoint, uno per ogni lingua localizzata.

     Usare lo stesso nome di base per ogni file di risorse localizzato, ma aggiungere l'ID delle impostazioni cultura. Ad esempio, nome un tedesco localizzata resource *MyAppResources.de-. resx*.

4. Aprire ogni file di risorse e aggiungere le stringhe localizzate. Utilizzare gli stessi ID di stringa in ogni file.

5. Modificare il valore della **tipo di distribuzione** proprietà di ogni file di risorse da **AppGlobalResource** per fare in modo ogni file venga distribuito nella cartella App_GlobalResources del server.

6. Lasciare il valore di **Build Action** proprietà di ogni file impostato **risorsa incorporata**.

     Le risorse incorporate vengono compilate nella DLL del progetto.

7. Compilare il progetto per creare la risorsa DLL satellite.

8. Nel **Progettazione pacchetti**, scegliere il **avanzate** scheda e quindi aggiungere l'assembly satellite.

9. Nel **ubicazione** casella, anteporre una cartella con l'ID delle impostazioni cultura al percorso, ad esempio *de-DE\\\<nome elemento di progetto >. Resources*.

10. Se la soluzione non fa già riferimento all'assembly System. Web, aggiungere un riferimento a esso e aggiungere una direttiva nel codice per <xref:System.Web>.

11. Individuare tutte le stringhe hardcoded nel codice visibili agli utenti, ad esempio il testo dell'interfaccia utente, errori e testo del messaggio. Sostituirle con una chiamata al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Scegliere il **F5** chiave per compilare ed eseguire l'applicazione.

13. In SharePoint, cambiare la lingua di visualizzazione da quello predefinito.

     Le stringhe localizzate visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve avere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedere anche
- [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
