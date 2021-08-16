---
title: 'Procedura: Localizzare il codice | Microsoft Docs'
description: Informazioni su come localizzare il codice SharePoint sostituendo stringhe hard-coded con chiamate a GetGlobalResourceObject, un metodo che fa riferimento alle risorse localizzate.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a3cb812003543571bcd6fc2fea9307cc725247c8347aa4f108cdb7b494adb995
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367512"
---
# <a name="how-to-localize-code"></a>Procedura: Localizzare il codice
  Il codice non localizzato usa valori stringa hard-coded. Per localizzare le stringhe di codice, sostituirle con chiamate a , ovvero <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> un metodo che fa riferimento alle risorse localizzate.

## <a name="localize-code"></a>Localizzare il codice

#### <a name="to-localize-code"></a>Per localizzare il codice

1. In **Esplora soluzioni** aprire il menu di scelta rapida per un elemento di progetto e quindi scegliere **Aggiungi**  >  **modulo**.

     Scegliere il **modello File di** risorse.

    > [!NOTE]
    > Assicurarsi di aggiungere il file di risorse a un SharePoint di progetto in modo che la proprietà Tipo di distribuzione sia disponibile. Questa proprietà è necessaria più avanti in questa procedura.

2. Assegnare al file di risorse della lingua predefinito un nome a scelta aggiunto con un'estensione *resx,* ad esempio *MyAppResources.resx*.

3. Ripetere i passaggi 1 e 2 per aggiungere file di risorse separati all'elemento di progetto SharePoint, uno per ogni lingua localizzata.

     Usare lo stesso nome di base per ogni file di risorse localizzato, ma aggiungere l'ID impostazioni cultura. Ad esempio, assegnare un nome a una risorsa localizzata *MyAppResources.de-DE.resx*.

4. Aprire ogni file di risorse e aggiungere stringhe localizzate. Utilizzare gli stessi ID di stringa in ogni file.

5. Modificare il valore della proprietà **Tipo** di distribuzione di ogni file di risorse in **AppGlobalResource** per fare in modo che ogni file sia distribuito nella cartella App_GlobalResources del server.

6. Lasciare il valore della **proprietà Azione di** compilazione di ogni file come Risorsa **incorporata**.

     Le risorse incorporate vengono compilate nella DLL del progetto.

7. Compilare il progetto per creare le DLL satellite della risorsa.

8. In **Progettazione pacchetti scegliere** la **scheda Avanzate** e quindi aggiungere l'assembly satellite.

9. Nella casella **Percorso** anteporre una cartella ID impostazioni cultura al percorso percorso, ad esempio *de-DE \\ \<Project Item Name>.resources.dll*.

10. Se la soluzione non fa già riferimento all'assembly System.Web, aggiungere un riferimento all'assembly e aggiungere una direttiva nel codice a <xref:System.Web> .

11. Individuare tutte le stringhe hardcoded nel codice visibili agli utenti, ad esempio il testo dell'interfaccia utente, errori e testo del messaggio. Sostituirle con una chiamata al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Scegliere il **tasto F5** per compilare ed eseguire l'applicazione.

13. In SharePoint modificare la lingua di visualizzazione rispetto all'impostazione predefinita.

     Le stringhe localizzate vengono visualizzate nell'applicazione. Per visualizzare le risorse localizzate, SharePoint server deve essere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedi anche
- [Localizzare SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
