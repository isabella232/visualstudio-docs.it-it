---
title: Localizzazione di ClickOnce applicazioni | Microsoft Docs
description: Informazioni su tre modi per localizzare l'applicazione ClickOnce a una versione appropriata per impostazioni cultura specifiche.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 97756456d192921c2fff4ef9f283a89e775165c1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709888"
---
# <a name="localize-clickonce-applications"></a>Localizzazione delle applicazioni ClickOnce
La localizzazione è il processo di adattamento di un'applicazione a impostazioni cultura specifiche. Questo processo consiste nel tradurre il testo dell'interfaccia utente in una lingua specifica di un paese/regione, usare la formattazione di data e valuta corretta, regolare la dimensione dei controlli di un form e, se necessario, eseguire il mirroring dei controlli da destra verso sinistra.

 La localizzazione di un'applicazione comporta la creazione di uno o più assembly satellite. In ogni assembly sono contenute stringhe dell'interfaccia utente, immagini e altre risorse specifiche di determinate impostazioni cultura. Nel file eseguibile principale dell'applicazione sono contenute le stringhe delle impostazioni cultura predefinite dell'applicazione.

 Questo argomento descrive tre modi in cui è possibile distribuire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per altre impostazioni cultura:

- Includere tutti gli assembly satellite in una sola distribuzione.

- Generare una distribuzione per le singole impostazioni cultura, con un solo assembly satellite incluso in ognuna di esse.

- Scaricare gli assembly satellite su richiesta.

## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Inclusione di tutti gli assembly satellite in una sola distribuzione
 Anziché pubblicare più distribuzioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile pubblicare una sola distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contenente tutti gli assembly satellite.

 Questo metodo rappresenta il metodo predefinito in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per usarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è necessario effettuare operazioni aggiuntive.

 Per usare questo metodo con *MageUI.exe* è necessario configurare le impostazioni cultura per l'applicazione su **neutral** in *MageUI.exe*. e quindi includere manualmente tutti gli assembly satellite nella distribuzione. In *MageUI.exe* è possibile aggiungere gli assembly satellite usando il pulsante **Popola** nella scheda **File** del manifesto dell'applicazione.

 Il vantaggio di questo approccio è dato dalla possibilità di creare un'unica distribuzione e di semplificare il processo della distribuzione localizzata. In fase di esecuzione verrà usato l'assembly satellite appropriato, a seconda delle impostazioni cultura predefinite del sistema operativo Windows dell'utente. L'inconveniente di questo approccio riguarda il fatto che, ogni volta che l'applicazione viene installata o aggiornata in un computer client, vengono scaricati tutti gli assembly satellite. Se nell'applicazione è contenuto un numero elevato di stringhe o i clienti hanno una connessione di rete lenta, questo processo può influire sulle prestazioni durante l'aggiornamento dell'applicazione.

> [!NOTE]
> Con questo approccio si presuppone che l'applicazione regoli automaticamente l'altezza, la larghezza e la posizione dei controlli per adattare dimensioni diverse delle stringhe di testo nelle varie impostazioni cultura. In Windows Form è disponibile un'ampia gamma di controlli e tecnologie che consentono di progettare il form in modo da facilitarne la localizzazione, inclusi i controlli <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> e la proprietà <xref:System.Windows.Forms.Control.AutoSize%2A>.  Vedere anche Procedura: Supportare la localizzazione nei Windows [usando AutoSize e il controllo TableLayoutPanel](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).

## <a name="generate-one-deployment-for-each-culture"></a>Generare una distribuzione per le singole impostazioni cultura
 In questa strategia di distribuzione vengono generate più distribuzioni. In ogni distribuzione viene incluso solo l'assembly satellite necessario per impostazioni cultura specifiche e la distribuzione viene contrassegnata come specifica di tali impostazioni cultura.

 Per usare questo metodo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], impostare la proprietà **Lingua di pubblicazione** nella scheda **Pubblica** sul paese/regione desiderato. L'assembly satellite richiesto per il paese/regione selezionato verrà incluso automaticamente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e tutti gli altri assembly satellite verranno esclusi dalla distribuzione.

 È possibile eseguire la stessa operazione usando lo *strumentoMageUI.exe* in Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Usare il pulsante **Popola** nella scheda **File** del manifesto dell'applicazione per escludere tutti gli altri assembly satellite dalla directory dell'applicazione, quindi impostare il campo **Impostazioni cultura** nella scheda **Nome** per il manifesto della distribuzione in *MageUI.exe*. Questi passaggi non consentono solo di includere l'assembly satellite corretto, ma anche di impostare l'attributo `language` dell'elemento `assemblyIdentity` nel manifesto della distribuzione sul valore delle impostazioni cultura corrispondenti.

 Dopo aver pubblicato l'applicazione, è necessario ripetere questo passaggio per tutte le impostazioni cultura aggiuntive supportate dall'applicazione. La pubblicazione deve essere eseguita ogni volta in una directory di server Web o in una directory di condivisione file diversa, perché ogni manifesto dell'applicazione farà riferimento a un assembly satellite diverso e ogni manifesto della distribuzione avrà un valore diverso per l'attributo `language`.

## <a name="download-satellite-assemblies-on-demand"></a>Scaricare gli assembly satellite su richiesta
 Se si decide di includere tutti gli assembly satellite in un'unica distribuzione, è possibile migliorare le prestazioni usando il download su richiesta, che consente di contrassegnare gli assembly come facoltativi. Gli assembly contrassegnati non verranno scaricati quando viene installata o aggiornata l'applicazione. Sarà possibile installarli in qualunque momento chiamando il metodo <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> nella classe <xref:System.Deployment.Application.ApplicationDeployment>.

 Il download degli assembly satellite su richiesta differisce leggermente dal download degli altri tipi di assembly su richiesta. Per altre informazioni ed esempi di codice su come abilitare questo scenario mediante il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] degli strumenti per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).

 Questo scenario può essere attivato anche in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vedere anche [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) o [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

## <a name="testing-localized-clickonce-applications-before-deployment"></a>Verifica delle applicazioni ClickOnce localizzate prima della distribuzione
 Un assembly satellite verrà usato per un'applicazione Windows Forms solo se la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> per il thread principale dell'applicazione è impostata sulle impostazioni cultura dell'assembly satellite. È probabile che i clienti nei mercati locali eseguano già una versione localizzata di Windows con il valore predefinito appropriato specificato per le impostazioni cultura.

 Sono disponibili tre opzioni per la verifica delle distribuzioni localizzate prima di rendere disponibile l'applicazione ai clienti:

- È possibile eseguire l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nelle versioni localizzate appropriate di Windows.

- È possibile impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> a livello di codice nell'applicazione. Questa proprietà deve essere impostata prima di chiamare il metodo <xref:System.Windows.Forms.Application.Run%2A>.

## <a name="see-also"></a>Vedi anche
- [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Globalizzazione di Windows moduli](/dotnet/framework/winforms/advanced/globalizing-windows-forms)