---
title: Scrivere ed eseguire il debug del codice XAML usando Ricaricamento rapido XAML
description: Ricaricamento rapido XAML, o modifica e continuazione XAML, consente di apportare modifiche al codice XAML durante l'esecuzione di app
ms.date: 09/22/2021
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.custom: contperf-fy22q1
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: b1f7e3703bd3bb7fa907c926f62fa9b82ad2ce96
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430623"
---
# <a name="xaml-hot-reload-write-and-debug-your-wpf-and-uwp-apps-while-theyre-running"></a>Ricaricamento rapido XAML: scrivere ed eseguire il debug delle app WPF e UWP mentre sono in esecuzione

Con Ricaricamento rapido XAML, è possibile compilare e testare in modo incrementale il codice XAML con il vantaggio del contesto dati dell'app in esecuzione, dello stato di autenticazione e di altre complessità reali difficili da simulare durante la fase di progettazione.

> [!TIP]
> Se si è arrivati qui tramite l'interfaccia utente Ricaricamento rapido XAML, benvenuti. Si è nel posto giusto per altre informazioni su Ricaricamento rapido XAML. Se tuttavia è necessaria assistenza per la risoluzione dei Ricaricamento rapido XAML, vedere [Risoluzione dei](xaml-hot-reload-troubleshooting.md) Ricaricamento rapido XAML.

Disponibile sia in Visual Studio che Blend per Visual Studio, Ricaricamento rapido XAML particolarmente utile in questi scenari:

* Correzione dei problemi dell'interfaccia utente rilevati nel codice XAML dopo l'avvio dell'app in modalità di debug.

* Creazione di un nuovo componente dell'interfaccia utente per un'app in fase di sviluppo, sfruttando al tempo stesso il contesto di runtime dell'app.

|Tipi di applicazione supportati|Sistema operativo e strumenti|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ e .NET Core</br>Windows 7 e versioni successive |
|App Windows universali (UWP)|Windows 10 e versioni successive, con Windows 10 [SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ |

> [!NOTE]
> Se si usa Xamarin.Forms, vedere [Ricaricamento rapido XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

L'animazione seguente illustra un'istanza dell'uso della struttura ad albero visuale animata per aprire codice sorgente e quindi Ricaricamento rapido XAML per modificare il testo e il colore di un pulsante.

:::image type="content" source="../debugger/media/xaml-hot-reload-using.gif" alt-text="Animazione dell'albero visuale live che apre il codice sorgente e usa Ricaricamento rapido XAML per modificare gli elementi dell'interfaccia utente.":::

> [!NOTE]
> Visual Studio Ricaricamento rapido XAML è attualmente supportato solo quando si esegue un'applicazione in Visual Studio o Blend per Visual Studio con il debugger collegato (**F5** o **Avvia debug**). Non è possibile abilitare questa esperienza usando Collega a [processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) a meno che non si imposta [manualmente una variabile di ambiente](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Limitazioni note

Di seguito sono riportate alcune limitazioni note Ricaricamento rapido XAML. Per aggirare qualsiasi limitazione, è sufficiente arrestare il debugger e quindi completare l'operazione.

|Limitazione|WPF|UWP|Note|
|-|-|-|-|
|Cablamento di eventi ai controlli mentre l'app è in esecuzione|Non supportato|Non supportato|Vedere l'errore: *Assicurarsi che l'evento non sia riuscito.* Si noti che in WPF è possibile fare riferimento a un gestore eventi esistente. Nelle app UWP non è supportato il riferimento a un gestore eventi esistente.|
|Creazione di oggetti risorsa in un dizionario risorse, ad esempio quelli nella pagina o nella finestra dell'app o *in App.xaml*|Supportato a partire Visual Studio 2019 [versione 16.2](/visualstudio/releases/2019/release-notes-v16.2) e successive|Supportato|Esempi: <br>- Aggiunta di un `SolidColorBrush` oggetto in un dizionario risorse da usare come `StaticResource` .</br>Nota: le risorse statiche, i convertitori di stile e altri elementi scritti in un dizionario risorse possono essere applicati/usati durante l'Ricaricamento rapido XAML. Non è supportata solo la creazione della risorsa.</br> - Modifica della proprietà del dizionario `Source` risorse.|
|Aggiunta di nuovi controlli, classi, finestre o altri file al progetto mentre l'app è in esecuzione|Non supportato|Non supportato|Nessuno|
|Gestione NuGet pacchetti (aggiunta/rimozione/aggiornamento di pacchetti)|Non supportato|Non supportato|Nessuno|
|Modifica data binding che usa l'estensione di markup {x:Bind}|N/A|Supportato a partire Visual Studio 2019|Questa operazione richiede Windows 10 versione 1809 (build 10.0.17763). Non supportato in Visual Studio 2017 o versioni precedenti.|
|La modifica delle direttive x:Uid non è supportata|N/D|Non supportato|Nessuno|
|Uso di più processi | Supportato | Supportato | Supportato in Visual Studio 2019 [versione 16.6 e](/visualstudio/releases/2019/release-notes-v16.6) successive. |

## <a name="error-messages"></a>messaggi di errore

È possibile che si sia verificati gli errori seguenti durante l'Ricaricamento rapido XAML.

|Messaggio di errore|Descrizione|
|-|-|
|Verificare che l'evento non sia riuscito|L'errore indica che si sta tentando di collegare un evento a uno dei controlli, che non è supportato durante l'esecuzione dell'applicazione.|
|Questa modifica non è supportata da Ricaricamento rapido XAML e non verrà applicata durante la sessione di debug.|L'errore indica che la modifica che si sta tentando di eseguire non è supportata da Ricaricamento rapido XAML. Arrestare la sessione di debug, apportare la modifica e quindi riavviare la sessione di debug.  |

Se si trova uno scenario non supportato che si desidera visualizzare supportato, indicarlo usando l'opzione Suggerisci [una](../ide/suggest-a-feature.md) funzionalità.

## <a name="see-also"></a>Vedi anche

* [Risoluzione dei problemi relativi al ricaricamento rapido XAML](xaml-hot-reload-troubleshooting.md)
* [Ricaricamento rapido XAML per Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
