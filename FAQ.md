# Frequently asked questions

## Product connections and scope

### How are Business Continuity center, Advisor, and Operations Center connected?

**Advisor** provides recommendations across all Well-Architected Framework (WAF) pillars beyond just Reliability. It's the entry point for customers who want a holistic view of how to improve reliability, security, cost efficiency, and more.

**Resiliency Center (within Business Continuity center)** narrows the focus to zonal resiliency. It introduces functionality that Advisor doesn't currently have:

- Defining Service Groups
- Setting resiliency goals
- Tracking progress toward those goals

Its unique value is the goal-based view: customers can see exactly which recommendations they need to implement to achieve a resiliency target for their application.

**Operations Center** is the unified operational platform. It spans multiple domains (observability, optimization, security, configuration, and resiliency):

- Resiliency Center is one experience inside Operations Center
- The Resiliency Center UI and data model are replicated across Resiliency Center and Operations Center, ensuring data consistency and a seamless experience across products

> [!NOTE]
> Advisor is comprehensive across pillars. Resiliency Center is goal-driven and application-focused on resiliency. Operations Center is the umbrella platform that integrates these experiences alongside other operational capabilities.

### What is the incremental value of using Resiliency Center?

**Self-service enablement**: Customers can independently define Service Groups and set resiliency goals. This reduces reliance on Microsoft account teams to scope workloads, accelerating time-to-value.

**Goal-based resiliency tracking**: Unlike Advisor's broad recommendation set, Resiliency Center provides a goal-oriented view. Customers can see exactly where they stand against zonal resiliency adoption and identify gaps.

**Complementary to WARA**: Resiliency Center doesn't replace WARA — it currently covers only zonal resiliency recommendations. Instead, it complements WARA by providing a lightweight, self-serve experience that helps customers operationalize resiliency improvements between WARA engagements.

## Recommendations coverage

### Which recommendations are included in the Private Preview?

- Zonal resiliency recommendations for [supported services](./Goals%20and%20recommendations/Recommendations.md#Recommendation-reference)
- Expansion to additional services planned in upcoming phases

### How should I prioritize recommendations coming from WARA versus Resiliency Center?

**WARA** delivers the most comprehensive, field-led review, covering all resiliency categories (not just zonal). Recommendations from WARA reflect deeper engagement and broader coverage.

**Resiliency Center** acts as the self-serve complement to WARA. It provides zonal resiliency recommendations for selected services, especially valuable for workloads that haven't yet gone through WARA. Through Resiliency Center, customers get their first self-service experience to view goal-linked recommendations and act more easily. While today it's scoped to zonal resiliency, it will expand to additional resiliency categories in future releases.

### If I complete recommendations in Resiliency Center, will they sync back to Advisor?

Yes. Recommendations resolved in Resiliency Center are also reflected in Advisor.

## Service Groups and workload definitions

### After onboarding a Service Group, can I still collaborate with Microsoft field teams on WARA reviews?

Yes. Field teams remain available for WARA reviews and ongoing support in parallel with Resiliency Center.

### Why do I have to go to two places for recommendations? I just want a single, consolidated view

Eventually, you'll see the full list of recommendations in Advisor based on Service Group definitions. Until then, the Service Group construct is only supported for zonal recommendations in Resiliency Center.

### I want to convert an existing Microsoft-defined workload into a Service Group. How can I do that?

Currently, there's no way to convert Microsoft (field-defined) workloads into Service Groups.

### How much time will it take to create Service Groups and set goals before I start seeing recommendations?

> [!NOTE]
> It can take around 2 hours for the recommendations for the assigned goal to be visible after Service Group is created.
