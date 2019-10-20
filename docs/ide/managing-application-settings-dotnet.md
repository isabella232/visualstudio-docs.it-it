---
title: Gestire le impostazioni dell'applicazione (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4215987ee0a61935efe27ab927d826cc1c6ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654628"
---
# <a name="manage-application-settings-net"></a>Gestire le impostazioni dell'applicazione (.NET)

Le impostazioni dell'applicazione consentono di archiviare le informazioni sull'applicazione in modo dinamico. Le impostazioni consentono di archiviare nel computer client le informazioni che non devono essere incluse nel codice dell'applicazione (ad esempio una stringa di connessione), le preferenze dell'utente e altre informazioni necessarie in fase di esecuzione.

Le impostazioni dell'applicazione sostituiscono le proprietà dinamiche usate nelle versioni precedenti di Visual Studio.

Ogni impostazione dell'applicazione deve avere un nome univoco. Tale nome può essere formato da una combinazione di lettere, numeri o un carattere di sottolineatura, non può iniziare con un numero e non può avere spazi. Il nome viene modificato tramite la proprietà `Name`.

Le impostazioni dell'applicazione possono essere archiviate come qualsiasi tipo di dati che viene serializzato come XML che abbia un oggetto `TypeConverter` che implementa `ToString`/`FromString`. I tipi più comuni sono `String`, `Integer` e `Boolean`, ma è anche possibile archiviare i valori come <xref:System.Drawing.Color>, <xref:System.Object> o come una stringa di connessione.

Anche le impostazioni dell'applicazione mantengono un valore. Il valore viene impostato con la proprietà **Valore** e deve corrispondere al tipo di dati dell'impostazione.

Inoltre, in fase di progettazione, è possibile associare le impostazioni dell'applicazione alla proprietà di un form o di un controllo.

Sono disponibili due tipi di impostazioni dell'applicazione, in base all'ambito:

- Le impostazioni con ambito di applicazione possono essere usate per informazioni quali un URL per un servizio Web o una stringa di connessione del database. Questi valori sono associati all'applicazione. Di conseguenza, gli utenti non possono modificarli in fase di esecuzione.

- Le impostazioni con ambito di utente possono essere usate per informazioni quali la memorizzazione dell'ultima posizione di un form oppure una preferenza su un tipo di carattere. Gli utenti possono modificare questi valori in fase di esecuzione.

È possibile modificare il tipo di un'impostazione usando la proprietà **Ambito** .

Il sistema del progetto archivia le impostazioni dell'applicazione in due file XML:

- un file *app.config*, creato in fase di progettazione quando si crea la prima impostazione dell'applicazione

- un file *user.config*, creato in fase di esecuzione quando l'utente che esegue l'applicazione modifica il valore di un'impostazione utente.

Le modifiche apportate alle impostazioni utente non vengono scritte su disco a meno che nell'applicazione non venga specificamente chiamato un metodo che esegua questa operazione.

## <a name="create-application-settings-at-design-time"></a>Creare impostazioni dell'applicazione in fase di progettazione

In fase di progettazione, le impostazioni dell'applicazione possono essere create in due modi, mediante la pagina **Impostazioni** di **Creazione progetti**oppure mediante la finestra **Proprietà** per un form o un controllo, che consente di associare un'impostazione direttamente a una proprietà.

Quando si crea un'impostazione con ambito di applicazione, ad esempio una stringa di connessione del database oppure un riferimento a risorse del server, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tale impostazione viene salvata nel file *app.config* con il tag `<applicationSettings>`. (Le stringhe di connessione vengono salvate nel tag `<connectionStrings>` .)

Quando si crea un'impostazione con ambito di utente, ad esempio il tipo di carattere predefinito, la pagina iniziale o le dimensioni delle finestre, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tale impostazione viene salvata nel file *app.config* con il tag `<userSettings>`.

> [!IMPORTANT]
> Quando si archiviano stringhe di connessione in *app.config*, è opportuno adottare delle precauzioni per evitare di rivelare informazioni riservate, quali password o percorsi del server, nella stringa di connessione.
>
> Se si ricevono informazioni della stringa di connessione da un'origine esterna, quale un utente che immette un ID utente e una password, accertarsi che tra i valori usati per costruire la stringa di connessione non siano presenti parametri aggiuntivi in grado di modificare il comportamento della connessione.
>
> Valutare l'uso della funzionalità di configurazione protetta per crittografare le informazioni riservate nel file di configurazione. Per altre informazioni, vedere [Proteggere le informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Poiché non è presente alcun modello di file di configurazione per le librerie di classi, le impostazioni dell'applicazione non si applicano ai progetti Libreria di classi, ad eccezione dei progetti DLL di Visual Studio Tools per Office che possono avere un file di configurazione.

## <a name="use-customized-settings-files"></a>Usare file di impostazioni personalizzati

È possibile aggiungere file di impostazioni personalizzati al progetto per agevolare la gestione dei gruppi di impostazioni. Le impostazioni contenute in un unico file vengono caricate e salvate come unità. L'archiviazione delle impostazioni in file diversi per i gruppi di utilizzo frequente e di utilizzo non frequente può determinare un risparmio di tempo nel caricamento e nel salvataggio delle impostazioni.

Ad esempio, è possibile aggiungere un file quale *SpecialSettings.settings* al progetto. Mentre la classe `SpecialSettings` non è esposta nello spazio dei nomi `My` , **Visualizza codice** può leggere il file di impostazioni personalizzate contenente `Partial Class SpecialSettings`.

La **finestra di progettazione delle impostazioni** cerca innanzitutto il file *Settings. Settings* creato dal sistema del progetto; Questo file è il file predefinito visualizzato in **Progettazione progetti** nella scheda **Impostazioni** . *Settings. Settings* si trova nella cartella *progetto* per i progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e nella cartella *Proprietà* per i progetti [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Successivamente, **Creazione progetti** cerca gli altri file di impostazioni nella cartella radice del progetto. Pertanto, è necessario inserirvi il file di impostazioni personalizzato. Se si aggiunge un file *.settings* in un altro punto del progetto, questo non verrà trovato da **Creazione progetti**.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Accedere o modificare le impostazioni dell'applicazione in fase di esecuzione in Visual Basic

Nei progetti Visual Basic è possibile accedere alle impostazioni dell'applicazione in fase di esecuzione usando l'oggetto `My.Settings`. Nella pagina **Impostazioni** fare clic sul pulsante **Visualizzare codice** per visualizzare il file *Settings.vb*. Nel file *Settings.vb* viene definita la classe `Settings` che consente di gestire i seguenti eventi nella classe delle impostazioni: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, e <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. La classe `Settings` nel file *Settings.vb* è una classe parziale in cui viene visualizzato solo il codice di proprietà dell'utente, non l'intera classe generata. Per altre informazioni sull'accesso alle impostazioni dell'applicazione usando l'oggetto `My.Settings`, vedere [Accedere alle impostazioni dell'applicazione (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

I valori di qualsiasi impostazione con ambito di utente che vengono modificati dall'utente in fase di esecuzione, ad esempio la posizione di un form, vengono archiviati in un file *user.config*. I valori predefiniti vengono salvati nel file *app.config*.

Se è stata modificata qualsiasi impostazione con ambito di utente in fase di esecuzione, ad esempio durante il test dell'applicazione, e si desidera ripristinare i valori predefiniti per queste impostazioni, scegliere il pulsante **Sincronizza**.

È consigliabile usare l'oggetto `My.Settings` e il file *.settings* predefinito per accedere alle impostazioni. Ciò perché è possibile usare **Progettazione impostazioni** per assegnare proprietà alle impostazioni e le impostazioni utente vengono salvate automaticamente prima della chiusura dell'applicazione. L'applicazione Visual Basic può comunque accedere direttamente alle impostazioni. In quel caso è necessario accedere alla classe `MySettings` e usare un file *.settings* personalizzato nella radice del progetto. È necessario salvare le impostazioni utente prima di terminare l'applicazione, come per le applicazioni C#, come illustrato nella sezione seguente.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Accedere o modificare le impostazioni dell'applicazione in fase di esecuzione in C#
<!-- markdownlint-enable MD003 MD020 -->

In linguaggi diversi da Visual Basic, ad esempio C#, è necessario accedere direttamente alla classe `Settings`, come illustrato nell'esempio seguente relativo a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

È necessario chiamare in modo esplicito il metodo `Save` di questa classe wrapper per rendere persistenti le impostazioni utente. Questa operazione viene generalmente effettuata nel gestore eventi `Closing` del form principale. Nell'esempio seguente di C# viene illustrata una chiamata al metodo `Save`.

```csharp
Properties.Settings.Default.Save();
```

Per informazioni generali sull'accesso alle impostazioni dell'applicazione attraverso la classe `Settings`, vedere [Cenni preliminari sulle impostazioni delle applicazioni (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Per impostazioni sullo scorrimento delle impostazioni, vedere questo [post del forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Vedere anche

- [Accedere alle impostazioni dell'applicazione (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
