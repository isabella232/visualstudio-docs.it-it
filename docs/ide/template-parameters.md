---
title: Parametri dei modelli di progetti ed elementi
description: Informazioni su come usare i parametri del modello per sostituire i valori nel modello quando viene creata un'istanza del modello.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 55f8d161eff6b1df3395a8819bba4064c5a7c4af3172e77c7669a3d3b2b340f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411815"
---
# <a name="template-parameters"></a>Parametri di modelli

Quando viene creata un'istanza di modello, è possibile sostituire i valori nel modello. Per configurare questa funzionalità, usare *parametri del modello*. Parametri del modello è utilizzabile per sostituire i valori, ad esempio i nomi della classe e gli spazi dei nomi nel modello. La creazione guidata del modello che viene eseguito in background quando un utente aggiunge un nuovo elemento o progetto sostituisce questi parametri.

## <a name="declare-and-enable-template-parameters"></a>Dichiarare e abilitare i parametri di modello

I parametri di modello vengono dichiarati nel formato $*parametro*$. Esempio:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Abilitare la sostituzione dei parametri nei modelli

1. Nel file *con estensione vstemplate* del modello individuare l'elemento corrispondente all'elemento per cui si vuole abilitare `ProjectItem` la sostituzione dei parametri.

1. Impostare l'attributo `ReplaceParameters` dell'elemento `ProjectItem` su `true`.

1. Includere i parametri nella posizione appropriata nel file di codice per l'elemento del progetto. Ad esempio, il parametro seguente specifica che deve essere usato il nome di progetto sicuro per lo spazio dei nomi in un file:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parametri di modello riservati

La tabella seguente elenca i parametri di modello riservati che possono essere usati da qualsiasi modello:

|Parametro|Descrizione|
|---------------|-----------------|
|clrversion|Versione corrente di Common Language Runtime (CLR).|
|ext_*|Aggiungere il prefisso `ext_` a tutti i parametri per fare riferimento alle variabili del modello padre. Ad esempio, `ext_safeprojectname`.|
|guid[1-10]|GUID usato per sostituire il GUID del progetto in un file di progetto. È possibile specificare fino a 10 GUID univoci, ad esempio `guid1`.|
|itemname|Nome del file in cui viene usato il parametro.|
|machinename|Nome del computer corrente, ad esempio Computer01.|
|projectname|Nome specificato dall'utente quando è stato creato il progetto.|
|registeredorganization|Valore della chiave del Registro di sistema da HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Spazio dei nomi radice del progetto corrente. Questo parametro è valido solo per i modelli di elemento.|
|safeitemname|Uguale a `itemname` ma con tutti i caratteri e gli spazi non sicuri sostituiti da caratteri di sottolineatura.|
|safeitemrootname|Uguale a `safeitemname`.|
|safeprojectname|Nome specificato dall'utente quando è stato creato il progetto con tutti i caratteri non sicuri e gli spazi rimossi.|
|time|L'ora corrente nel formato GG/MM/AAAA 00:00:00.|
|specifiedsolutionname|Nome della soluzione. Quando l'opzione per creare una directory di soluzione è selezionata, `specifiedsolutionname` è il nome della soluzione. Quando l'opzione per creare una directory di soluzione non è selezionata, `specifiedsolutionname` è vuoto.|
|userdomain|Dominio dell'utente corrente.|
|username|Nome dell'utente corrente.|
|webnamespace|Nome del sito Web corrente. Questo parametro viene usato nel modello di modulo Web per garantire che i nomi delle classi siano univoci. Se il sito Web si trova nella directory radice del server Web, questo parametro di modello viene risolto nella directory radice del server Web.|
|anno|L'anno corrente nel formato AAAA.|

> [!NOTE]
> I parametri di modello fanno distinzione tra maiuscole e minuscole.

## <a name="custom-template-parameters"></a>Parametri di modello personalizzati

Oltre ai parametri di modello riservati predefiniti usati durante la sostituzione dei parametri, è possibile specificare i propri valori e i propri parametri di modello. Per altre informazioni, vedere [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Esempio: usare il nome del progetto per un nome file

È possibile specificare nomi di file variabili per gli elementi del progetto usando un parametro nell'attributo `TargetFileName`.

L'esempio seguente specifica che il nome di un file eseguibile usi il nome del progetto, specificato da `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Esempio: usare il nome di progetto sicuro per il nome dello spazio dei nomi

Per usare il nome di progetto sicuro per lo spazio dei nomi in un file di classe C#, usare la sintassi seguente:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Nel file *.vstemplate* del modello di progetto includere l'attributo `ReplaceParameters="true"` quando si fa riferimento al file:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Vedi anche

- [Procedura: Sostituire parametri in un modello](how-to-substitute-parameters-in-a-template.md)
- [Personalizzare i modelli](../ide/customizing-project-and-item-templates.md)
- [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)
- [Riferimento allo schema di modello](../extensibility/visual-studio-template-schema-reference.md)
