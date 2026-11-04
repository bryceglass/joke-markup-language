# JML — Joke Markup Language

**An open markup language for the structure, intent, and performance of comedy.**

JML is an experimental, performer-agnostic format for representing jokes, bits, beats, delivery direction, and stage cues. Its central principle is **semantic direction by default, precise performance overrides when needed**.

JML is independent of any voice synthesis model, animation system, or production tool. [Pumpkin Theater](https://github.com/bryceglass/pumpkin-theater) is an early prospective consumer, not part of the language specification.

## A taste of JML

```xml
<routine id="smart-porch" version="0.1">
  <scene id="opening">
    <bit id="doorbells" premise="Smart technology makes life harder">
      <joke id="locked-out" form="setup-punch">
        <line character="comic">
          <setup>I bought a smart doorbell. It recognizes everybody.</setup>
          <pause ms="450"/>
          <punch id="payoff" intent="reversal">
            <attitude tone="deadpan">
              <delivery pace="slow">Now it won't let me in.</delivery>
            </attitude>
          </punch>
        </line>
        <react character="sidekick" emote="surprised"
               after="payoff.end" delay="400ms"/>
      </joke>
    </bit>
  </scene>
</routine>
```

The semantic elements describe *what the comedy is doing*. Optional delivery and timing instructions describe *how it should be performed*. Renderers may approximate unsupported directions but must not silently rewrite dialogue.

## Status

**JML v0.1 is an experimental draft, not a stable or validated standard.** The example illustrates intended syntax; formal grammar, schema, and conformance rules are still in development.

## Explore

- [Draft specification](spec/jml-0.1.md)
- [Design principles](docs/design-principles.md)
- [Prior art and interoperability](docs/prior-art.md)
- [Example JML routine](examples/smart-porch.jml)
- [Roadmap](docs/roadmap.md)
- [Contributing](CONTRIBUTING.md)
- [Enhancement proposals](proposals/README.md)

## Interoperability

JML is informed by [SSML](https://www.w3.org/TR/speech-synthesis11/), [EmotionML](https://www.w3.org/TR/emotionml/), [SMIL](https://www.w3.org/TR/SMIL3/), and authoring formats such as [Fountain](https://fountain.io/). These are influences, not claimed conformance.

## Licensing

Licensing for specification text, tools, and example performances will be clarified before the first tagged release. Contributions should be original or appropriately licensed.
