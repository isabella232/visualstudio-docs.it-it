---
title: Scarica assembly satellite su richiesta (API ClickOnce)
description: Informazioni su come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6ebcb455147b1cb014eb7aafc9f6a9e658e0131
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217008"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: scaricare assembly satellite su richiesta con l'API di distribuzione ClickOnce
Le applicazioni Windows Form possono essere configurate per più impostazioni cultura con l'uso di assembly satellite. Un *assembly satellite* è un assembly in cui sono contenute risorse dell'applicazione per impostazioni cultura diverse da quelle predefinite dell'applicazione.

 Come illustrato in [localizzare applicazioni ClickOnce](../deployment/localizing-clickonce-applications.md), è possibile includere più assembly satellite per più impostazioni cultura all'interno della stessa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scaricherà tutti gli assembly satellite nella distribuzione nel computer client, anche se probabilmente un singolo client richiederà un solo assembly satellite.

 Questa procedura dettagliata descrive come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti. La procedura seguente usa gli strumenti disponibili in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. È anche possibile eseguire questa attività in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vedere anche [procedura dettagliata: scaricare assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) o [procedura dettagliata: scaricare assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

> [!NOTE]
> Ai fini dell'esecuzione del test, l'esempio di codice seguente imposta a livello di codice le impostazioni cultura su `ja-JP`. Per informazioni su come modificare il codice per un ambiente di produzione, vedere la sezione "Passaggi successivi" più avanti in questo argomento.

## <a name="prerequisites"></a>Prerequisiti
 In questo argomento si presuppone che siano note le procedure per aggiungere risorse localizzate all'applicazione con Visual Studio. Per istruzioni dettagliate, vedere [procedura dettagliata: localizzare Windows Form](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Per scaricare gli assembly satellite su richiesta

1. Aggiungere il codice seguente all'applicazione per consentire il download degli assembly satellite su richiesta.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb" id="Snippet1":::

2. Generare assembly satellite per l'applicazione tramite [Resgen.exe (Generatore di file di risorse)](/dotnet/framework/tools/resgen-exe-resource-file-generator) o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Generare un manifesto dell'applicazione o aprire il manifesto dell'applicazione esistente usando *MageUI.exe*. Per altre informazioni su questo strumento, vedere [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. Scegliere la scheda **File** .

5. Scegliere il pulsante con i **puntini di sospensione** (**...**) e selezionare la directory contenente tutti gli assembly e file dell'applicazione, inclusi gli assembly satellite generati con *Resgen.exe*. Un assembly satellite avrà un nome nel formato *\<isoCode>\ApplicationName.resources.dll*, dove \<isoCode> è un identificatore di lingua in formato RFC 1766.

6. Fare clic su **Popola** per aggiungere i file alla distribuzione.

7. Selezionare la casella di controllo **Facoltativo** per ogni assembly satellite.

8. Impostare il campo di gruppo per ogni assembly satellite sul relativo identificatore di lingua ISO. Per un assembly satellite giapponese, ad esempio, specificare `ja-JP`. In questo modo il codice aggiunto nel passaggio 1 scaricherà l'assembly satellite appropriato, a seconda dell'impostazione della proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> dell'utente.

## <a name="next-steps"></a>Passaggi successivi
 In un ambiente di produzione sarà probabilmente necessario rimuovere la riga degli esempi di codice usata per impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> su un valore specifico, perché il valore predefinito per i computer client è quello corretto. Quando l'applicazione è in esecuzione su un computer client giapponese, ad esempio, la proprietà predefinita <xref:System.Threading.Thread.CurrentUICulture%2A> sarà `ja-JP` . L'impostazione di tale valore a livello di codice è un buon metodo per procedere alla verifica degli assembly satellite prima di distribuire l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Localizzazione delle applicazioni ClickOnce](../deployment/localizing-clickonce-applications.md)
