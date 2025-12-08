# Frequently asked questions

## Product connections and scope

### How are Resiliency experiences and Advisor connected?

**Advisor** provides recommendations across all Well-Architected Framework (WAF) pillars beyond just Reliability. It's the entry point for customers who want a holistic view of how to improve reliability, security, cost efficiency, and more.

**Resiliency in Azure** narrows the focus to zonal resiliency. It introduces additional functionality such as:

- Defining Service Groups
- Setting resiliency goals
- Tracking progress toward those goals

Its unique value is the goal-based view: customers can see exactly which Advisor recommendations they need to implement to achieve a resiliency target for their application.

### What is the incremental value of using Resiliency in Azure?

**Self-service enablement**: Customers can independently define Service Groups and set resiliency goals. This reduces reliance on Microsoft account teams to scope workloads, accelerating time-to-value.

**Goal-based resiliency tracking**: Unlike the Advisor's broad recommendation set, Resiliency in Azure provides a goal-oriented view. Customers can see exactly where they stand against zonal resiliency adoption and identify gaps.

**Complementary to WARA**: Resiliency in Azure doesn't replace WARA — it currently covers only zonal resiliency recommendations. Instead, it complements WARA by providing a lightweight, self-serve experience that helps customers operationalize resiliency improvements between WARA engagements.

## Recommendations coverage

### Which recommendations are included in the Private Preview?

- Zonal resiliency recommendations for [supported services](./Goals%20and%20recommendations/Recommendations.md#Recommendation-reference)
- Expansion to additional services planned in upcoming phases

### How should I prioritize recommendations coming from WARA versus Resiliency in Azure?

**WARA** delivers the most comprehensive, field-led review, covering all resiliency categories (not just zonal). Recommendations from WARA reflect deeper engagement and broader coverage.

**Resiliency in Azure** acts as the self-serve complement to WARA. It provides zonal resiliency recommendations for selected services, especially valuable for workloads that haven't yet gone through WARA. Through Resiliency experiences, customers get their first self-service experience to view goal-linked recommendations and act more easily. While today it's scoped to zonal resiliency, it will expand to additional resiliency categories in future releases.

### If I complete recommendations in Resiliency experiences, will they sync back to Advisor?

Yes. Recommendations resolved in Resiliency experiences are also reflected in Advisor.

## Service Groups and workload definitions

### After onboarding a Service Group, can I still collaborate with Microsoft field teams on WARA reviews?

Yes. Field teams remain available for WARA reviews and ongoing support in parallel with Resiliency in Azure.

### Why do I have to go to two places for recommendations? I just want a single, consolidated view

Eventually, you'll see the full list of recommendations in Advisor based on Service Group definitions. Until then, the Service Group construct is only supported for zonal recommendations in Resiliency experiences.

### I want to convert an existing Microsoft-defined workload into a Service Group. How can I do that?

Currently, there's no way to convert Microsoft (field-defined) workloads into Service Groups.

### How much time will it take to create Service Groups and set goals before I start seeing recommendations?

It can take around 2 hours for the recommendations for the assigned goal to be visible after the Service Group is created.
