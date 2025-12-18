# Client SDKs

We provide client libraries in a number of popular languages that make it easier to work with the Claude API.

---

This page includes brief installation instructions and links to the open-source GitHub repositories for Anthropic's Client SDKs. For basic usage instructions, see the [API reference](./api-overview.md) For detailed usage instructions, refer to each SDK's GitHub repository. 

<Note>
Additional configuration is needed to use Anthropic's Client SDKs through a partner platform. If you are using Amazon Bedrock, see [this guide](../developer/developer-build-with-claude-claude-on-amazon-bedrock.md); if you are using Google Cloud Vertex AI, see [this guide](../developer/developer-build-with-claude-claude-on-vertex-ai.md); if you are using Microsoft Foundry, see [this guide](../developer/developer-build-with-claude-claude-in-microsoft-foundry.md).
</Note>

## Python

[Python library GitHub repo](https://github.com/anthropics/anthropic-sdk-python)

**Requirements:** Python 3.8+

**Installation:**

```bash
pip install anthropic
```

---

## TypeScript

[TypeScript library GitHub repo](https://github.com/anthropics/anthropic-sdk-typescript)

<Info>
While this library is in TypeScript, it can also be used in JavaScript libraries.
</Info>

**Installation:**

```bash
npm install @anthropic-ai/sdk
```

---

## Java

[Java library GitHub repo](https://github.com/anthropics/anthropic-sdk-java)

**Requirements:** Java 8 or later

**Installation:**

Gradle:
```groovy
implementation("com.anthropic:anthropic-java:2.10.0")
```

Maven:
```xml
<dependency>
    <groupId>com.anthropic</groupId>
    <artifactId>anthropic-java</artifactId>
    <version>2.10.0</version>
</dependency>
```

---

## Go

[Go library GitHub repo](https://github.com/anthropics/anthropic-sdk-go)

**Requirements:** Go 1.22+

**Installation:**

```bash
go get -u 'github.com/anthropics/anthropic-sdk-go@v1.17.0'
```

---

## C#

[C# library GitHub repo](https://github.com/anthropics/anthropic-sdk-csharp)

<Info>
The C# SDK is currently in beta.
</Info>

**Requirements:** .NET 8 or later

**Installation:**

```bash
dotnet add package Anthropic
```

---

## Ruby

[Ruby library GitHub repo](https://github.com/anthropics/anthropic-sdk-ruby)

**Requirements:** Ruby 3.2.0 or later

**Installation:**

Add to your Gemfile:
```ruby
gem "anthropic", "~> 1.13.0"
```

Then run:
```bash
bundle install
```

---

## PHP

[PHP library GitHub repo](https://github.com/anthropics/anthropic-sdk-php)

<Info>
The PHP SDK is currently in beta.
</Info>

**Requirements:** PHP 8.1.0 or higher

**Installation:**

```bash
composer require "anthropic-ai/sdk 0.3.0"
```

---

## Beta namespace in client SDKs

Every SDK has a `beta` namespace that is available for accessing new features that Anthropic releases in beta versions. Use this in conjunction with [beta headers](./api-beta-headers.md) to access these features. Refer to each SDK's GitHub repository for specific usage examples.