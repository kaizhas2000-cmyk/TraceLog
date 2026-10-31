# TraceLog

**A flight recorder for the iOS Simulator that gives AI coding agents eyes at runtime.**

Native macOS menu-bar app. Local-first. Built for developers who ship iOS apps with AI coding agents (Claude Code, Cursor, Codex).

> **Status:** prototype in active development. Source code will be published in this repository.

## The problem

AI coding agents can write most of the code for an iOS app, but they are blind at runtime. When the app crashes, freezes or a network request fails in the iOS Simulator, the agent cannot see it. The developer becomes the bridge: reproduce the bug, copy Xcode logs, take screenshots, paste everything back into the AI. This loop repeats dozens of times a day and often fails because the agent gets incomplete context.

## How TraceLog works

1. TraceLog runs in the macOS menu bar and keeps a rolling local buffer of the iOS Simulator session: logs, network requests, crashes, user input and screen states on one timeline.
2. When a bug happens, press **Cmd+Shift+B**. The last seconds are frozen into a **Trace**, a structured, AI-readable debugging artifact.
3. The Trace is delivered to the AI agent through a built-in **MCP server**. The agent sees exactly what happened, finds the root cause and fixes it.

A Trace is also a clean bug report for humans: attach it to a ticket or send it to a teammate.

## Why it is different

| Tool | What it does | Where TraceLog fits |
|---|---|---|
| Sentry, Firebase Crashlytics | Crash monitoring in production | TraceLog works earlier, in the local dev loop |
| Proxyman, Charles | Network traffic only | TraceLog adds screen, input, logs and context |
| XcodeBuildMCP | Lets agents build and launch the Simulator | TraceLog records what actually happened |

TraceLog complements these tools rather than replacing them.

## Privacy

Local-first by design. Nothing is stored permanently and nothing leaves the Mac until the developer deliberately creates a Trace.

## Tech stack

Swift, SwiftUI, AppKit, ScreenCaptureKit, xcrun simctl, Apple unified logging, SQLite, Model Context Protocol (MCP).

## MVP scope

macOS + iOS Simulator only. No cloud, no accounts, no Android in the first version.

## Author

Olzhas Kairbek, Computer Science student at SDU (Kazakhstan). Solo founder.
