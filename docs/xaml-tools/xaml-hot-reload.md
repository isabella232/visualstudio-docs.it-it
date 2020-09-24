---
title: Scrivere ed eseguire il debug di XAML usando il ricaricamento a caldo di XAML
description: Il ricaricamento a caldo di XAML o la modifica e la continuazione di XAML consente di apportare modifiche al codice XAML durante l'esecuzione delle app
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b40da28cce9d2189b2f30ff6ea958926f3041836
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135079"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Scrivere ed eseguire il debug del codice XAML in esecuzione con il ricaricamento a caldo di XAML in Visual Studio

Il ricaricamento a caldo di XAML consente di compilare l'interfaccia utente dell'app WPF o UWP consentendo di apportare modifiche al codice XAML durante l'esecuzione dell'app. Il ricaricamento a caldo è disponibile sia in Visual Studio che in Blend per Visual Studio. Questa funzionalità consente di compilare e testare in modo incrementale il codice XAML con il vantaggio del contesto dei dati dell'app in esecuzione, dello stato di autenticazione e di altre complessità reali che è difficile simulare in fase di progettazione. Per informazioni sulla [risoluzione dei problemi relativi al](xaml-hot-reload-troubleshooting.md) ricaricamento a caldo di XAML, vedere.

> [!NOTE]
> Se si usa Novell. Forms, vedere [ricaricamento a caldo di XAML per Novell. Forms](/xamarin/xamarin-forms/xaml/hot-reload).

Il ricaricamento a caldo di XAML è particolarmente utile in questi scenari:

* Correzione dei problemi dell'interfaccia utente rilevati nel codice XAML dopo l'avvio dell'app in modalità di debug.

* Creazione di un nuovo componente dell'interfaccia utente per un'app in fase di sviluppo, sfruttando al contempo il contesto di runtime dell'app.

|Tipi di applicazioni supportati|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + e .NET Core</br>Windows 7 e versioni successive |
|App di Windows universale (UWP)|Windows 10 e versioni successive, con [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

La figura seguente illustra l'uso della struttura ad albero visuale attiva per aprire il codice sorgente e quindi il ricaricamento a caldo di XAML per modificare il testo del pulsante e il colore del pulsante.

![Ricaricamento rapido XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Il ricaricamento a caldo in XAML di Visual Studio è attualmente supportato solo quando si esegue l'applicazione in Visual Studio o Blend per Visual Studio con il debugger collegato (**F5** o **avviare il debug**). Non è possibile abilitare questa esperienza utilizzando [Connetti a processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) a meno che non si [imposti manualmente una variabile di ambiente](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono riportate le limitazioni note del ricaricamento a caldo di XAML. Per aggirare le limitazioni che si verificano, arrestare il debugger, quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Cablare gli eventi ai controlli durante l'esecuzione dell'app|Non supportato|Non supportate|Vedere errore: *assicurarsi che l'evento non sia riuscito*. Si noti che in WPF è possibile fare riferimento a un gestore eventi esistente. Nelle app UWP, il riferimento a un gestore eventi esistente non è supportato.|
|Creazione di oggetti risorsa in un dizionario risorse, ad esempio quelli nella pagina/finestra o nel file *app. XAML* dell'app.|Supportato a partire da Visual Studio 2019 Update 2|Supportato|Esempio: aggiunta di un oggetto a `SolidColorBrush` un dizionario risorse da utilizzare come `StaticResource` .</br>Nota: è possibile applicare/utilizzare risorse statiche, convertitori di stile e altri elementi scritti in un dizionario risorse durante l'utilizzo del ricaricamento a caldo di XAML. Solo la creazione della risorsa non è supportata.</br> Modifica della proprietà del dizionario risorse `Source` .|
|Aggiunta di nuovi controlli, classi, finestre o altri file al progetto durante l'esecuzione dell'app|Non supportato|Non supportato|nessuno|
|Gestione dei pacchetti NuGet (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|nessuno|
|Modifica data binding che usa l'estensione di markup {x:Bind}|N/D|Supportato a partire da Visual Studio 2019|Questa operazione richiede Windows 10 versione 1809 (Build 10.0.17763). Non supportato in Visual Studio 2017 o versioni precedenti.|
|La modifica delle direttive x:Uid non è supportata|N/D|Non supportato|nessuno|
|Più processi | Supportato | Supportato | Supportato in Visual Studio 2019 [versione 16,6](/visualstudio/releases/2019/release-notes-v16.6) e successive |

## <a name="error-messages"></a>messaggi di errore

È possibile che si verifichino gli errori seguenti durante l'utilizzo del ricaricamento a caldo di XAML.

|Messaggio di errore|Descrizione|
|-|-|
|Verifica evento non riuscita|Errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato mentre l'applicazione è in esecuzione.|
|Questa modifica non è supportata dal ricaricamento a caldo di XAML e non verrà applicata durante la sessione di debug.|Errore indica che la modifica che si sta tentando di eseguire non è supportata dal ricaricamento a caldo di XAML. Arrestare la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug. Se si trova uno scenario non supportato che si vuole visualizzare supportato, usare la nuova opzione "Suggerisci una funzionalità" nella community degli sviluppatori di [Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Vedere anche

* [Risoluzione dei problemi relativi al ricaricamento rapido XAML](xaml-hot-reload-troubleshooting.md)
* [Ricaricamento rapido XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
