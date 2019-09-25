---
title: 'CA1063: Implementare IDisposable correttamente'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8b29c9ed644c223488261333e79f17229bd4b7a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235293"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementare IDisposable correttamente

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

L' <xref:System.IDisposable?displayProperty=nameWithType> interfaccia non è implementata correttamente. Di seguito sono riportate alcune possibili cause:

- <xref:System.IDisposable>viene reimplementata nella classe.

- `Finalize`viene nuovamente sottoposto a override.

- `Dispose()`viene sottoposto a override.

- Il `Dispose()` metodo non è Public, [sealed](/dotnet/csharp/language-reference/keywords/sealed)o denominato **Dispose**.

- `Dispose(bool)`non è protetto, virtuale o non sealed.

- Nei tipi non sealed, `Dispose()` deve chiamare `Dispose(true)`.

- Per i tipi non sealed, `Finalize` l'implementazione non chiama `Dispose(bool)` né né né né il finalizzatore della classe di base.

La violazione di uno di questi modelli attiva CA1063 di avviso.

Ogni tipo non sealed che dichiara e implementa l' <xref:System.IDisposable> interfaccia deve fornire il proprio `protected virtual void Dispose(bool)` metodo. `Dispose()`deve chiamare `Dispose(true)`e il finalizzatore deve chiamare `Dispose(false)`. Se si crea un tipo non sealed che dichiara e implementa l' <xref:System.IDisposable> interfaccia, è necessario definirlo `Dispose(bool)` e chiamarlo. Per altre informazioni, vedere [pulire le risorse non gestite (Guida di .NET) e il](/dotnet/standard/garbage-collection/unmanaged) [modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Tutti <xref:System.IDisposable> i tipi devono implementare correttamente il [modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Esaminare il codice e determinare quale delle risoluzioni seguenti risolverà la violazione:

- Rimuovere <xref:System.IDisposable> dall'elenco di interfacce implementate dal tipo ed eseguire l'override dell'implementazione Dispose della classe di base.

- Rimuovere il finalizzatore dal tipo, eseguire l'override di Dispose (bool disposing) e inserire la logica di finalizzazione nel percorso del codice dove ' disposing ' è false.

- Eseguire l'override di Dispose (bool disposing) e inserire la logica di Dispose nel percorso del codice dove ' disposing ' è true.

- Assicurarsi che Dispose () sia dichiarato public e [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Rinominare il metodo Dispose in **Dispose** e verificare che sia dichiarato public e [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Assicurarsi che Dispose (bool) sia dichiarato come protected, Virtual e unsealed.

- Modificare Dispose () in modo che chiami Dispose (true), <xref:System.GC.SuppressFinalize%2A> quindi chiama sull'istanza dell'oggetto`this`corrente ( `Me` , o in Visual Basic), quindi restituisce.

- Modificare il finalizzatore in modo che chiami Dispose (false) e quindi restituisca.

- Se si crea un tipo non sealed che dichiara e implementa l' <xref:System.IDisposable> interfaccia, assicurarsi che l'implementazione di <xref:System.IDisposable> segua il modello descritto in precedenza in questa sezione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Esempio di pseudo-codice

Lo pseudo-codice seguente fornisce un esempio generale di implementazione di Dispose (bool) in una classe che utilizza risorse gestite e native.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Modello Dispose (linee guida per la progettazione di Framework)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Pulire le risorse non gestite (Guida di .NET)](/dotnet/standard/garbage-collection/unmanaged)