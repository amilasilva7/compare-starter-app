# Project Context Overview

This `GEMINI.md` file serves as the primary entry point for understanding the project's context and definition. The comprehensive project details have been organized into a structured folder system for improved maintainability and clarity.

**Rule:** Whenever 'context' is mentioned, it refers to all files within the `global_context` directory, encompassing both the `project_definition` and `development_guide` sections.

**Rule:** All actions and modifications must strictly comply with the entire project context as defined by all files within the `global_context` directory.

## How the Context is Organized

All detailed project documentation is now located within the `global_context/` directory. This directory contains two main sections:

1.  **Project Definition:** The core documentation outlining the project vision, features, user types, and technical considerations.
2.  **Development Guide:** Comprehensive instructions and best practices for developers.

### Main Sections:

*   **Project Definition:** The `project_definition/` folder is structured into the following top-level sections, providing a holistic view of the project's purpose and requirements:
    *   **Project Vision:** Outlines the core purpose and goals of the UK Price Comparison Website.
    *   **Key Features:** Details all functional and non-functional features, broken down by category.
    *   **User Types & Their Detailed Actions:** Describes each user role and their specific interactions with the application.
    *   **Target Audience:** Defines the primary users the application aims to serve.
    *   **Regulatory Compliance:** Covers all necessary legal and industry regulations, **including specific requirements from FCA, ICO (UK GDPR), CMA, and ASA for financial PCWs.**
    *   **Security Access Considerations:** Details the comprehensive security strategy for all user types.
    *   **Advanced Considerations & Future-Proofing:** Explores deeper requirements, operational aspects, and long-term strategic elements.
    *   **Non-Functional Requirements (NFRs):** Defines quantifiable quality attributes and operational characteristics, **including specific targets for performance, scalability, reliability, and security.**

*   **Development Guide:** The `development_guide/` folder provides detailed guidance for developers, covering the technical implementation and operational aspects of the project:
    *   **Project Overview:** High-level project summary and key business concepts.
    *   **Getting Started:** Prerequisites, **detailed local development setup using Docker Compose**, and making your first contribution.
    *   **Architecture & Tech Stack:** System architecture (microservices, BFF), technology choices (MERN + Kafka), and data flow.
    *   **Development Workflow:** Git, coding standards, **comprehensive testing strategy (Unit, Integration, E2E, Visual Regression, Accessibility)**, code reviews, and documentation.
    *   **Security Best Practices:** Secure coding, data handling, authentication/authorization, and AI security.
    *   **Deployment & Operations:** **Detailed CI/CD pipeline (GitHub Actions, pre/post-merge phases, approvals)**, deployment process, monitoring, and incident response.
    *   **API Design & Integration:** Principles for API design, **provider integration using Adapter/Factory patterns, and management of environment-specific third-party URLs/configurations.**
    *   **Data Management:** **MongoDB interaction, data migration strategy (`migrate-mongo`), master data management (Reference Data Service)**, and data quality.
    *   **UI/UX & Accessibility:** **Agoda-inspired design system, accessibility standards, frontend best practices (state management with RTK Query), and interactive content strategy.**
    *   **Troubleshooting & Support:** Common issues and how to get help.
    *   **SEO Strategy:** **Comprehensive playbook for web and AI engines, covering keywords, technical SEO, and content optimization.**
    
    ### Detailed Context File Structure
    
    To provide a comprehensive overview, here is the hierarchical structure of all context files within the `global_context` directory:
    
    **global_context/development_guide/**
    *   `README.md`
    *   `01_project_overview/01_key_business_concepts.md`
    *   `01_project_overview/README.md`
    *   `02_getting_started/01_prerequisites.md`
    *   `02_getting_started/02_local_development_setup.md`
    *   `02_getting_started/03_your_first_contribution.md`
    *   `02_getting_started/README.md`
    *   `03_architecture_tech_stack/01_high_level_architecture.md`
    *   `03_architecture_tech_stack/02_tech_stack_details.md`
    *   `03_architecture_tech_stack/03_data_flow_overview.md`
    *   `03_architecture_tech_stack/README.md`
    *   `04_development_workflow/01_git_workflow.md`
    *   `04_development_workflow/02_coding_standards_linting.md`
    *   `04_development_workflow/03_testing_strategy.md`
    *   `04_development_workflow/04_code_review_process.md`
    *   `04_development_workflow/05_documentation_guidelines.md`
    *   `04_development_workflow/README.md`
    *   `05_security_best_practices/00_security_strategy_overview.md`
    *   `05_security_best_practices/01_secure_coding_principles.md`
    *   `05_security_best_practices/02_data_handling_privacy.md`
    *   `05_security_best_practices/03_auth_auth_implementation.md`
    *   `05_security_best_practices/04_ai_security_considerations.md`
    *   `05_security_best_practices/README.md`
    *   `06_deployment_operations/01_ci_cd_pipeline.md`
    *   `06_deployment_operations/02_deployment_process.md`
    *   `06_deployment_operations/03_monitoring_logging.md`
    *   `06_deployment_operations/04_incident_response_role.md`
    *   `06_deployment_operations/05_performance_scalability.md`
    *   `06_deployment_operations/README.md`
    *   `07_api_design_integration/01_api_design_principles.md`
    *   `07_api_design_integration/02_provider_integration_guide.md`
    *   `07_api_design_integration/README.md`
    *   `08_data_management/01_database_interaction.md`
    *   `08_data_management/02_data_migration_strategy.md`
    *   `08_data_management/03_data_quality_governance.md`
    *   `08_data_management/04_master_data_management.md`
    *   `08_data_management/05_database_schema_design.md`
    *   `08_data_management/README.md`
    *   `09_ui_ux_accessibility/01_design_system_guidelines.md`
    *   `09_ui_ux_accessibility/02_accessibility_standards.md`
    *   `09_ui_ux_accessibility/03_frontend_best_practices.md`
    *   `09_ui_ux_accessibility/04_content_strategy.md`
    *   `09_ui_ux_accessibility/README.md`
    *   `10_troubleshooting_support/01_common_issues_faq.md`
    *   `10_troubleshooting_support/02_getting_help_escalation.md`
    *   `10_troubleshooting_support/README.md`
    *   `11_seo_strategy/01_seo_playbook.md`
    *   `11_seo_strategy/README.md`
    
    **global_context/project_definition/**
    *   `01_vision.md`
    *   `04_target_audience.md`
    *   `05_regulatory_compliance.md`
    *   `08_non_functional_requirements.md`
    *   `README.md`
    *   `02_key_features/01_core_comparison_car_insurance.md`
    *   `02_key_features/01_core_comparison.md`
    *   `02_key_features/02_data_personalization_frs.md`
    *   `02_key_features/02_data_personalization.md`
    *   `02_key_features/03_transparency_info_frs.md`
    *   `02_key_features/03_transparency_info.md`
    *   `02_key_features/04_rewards_loyalty_frs.md`
    *   `02_key_features/04_rewards_loyalty.md`
    *   `02_key_features/05_platform_tech.md`
    *   `02_key_features/06_monetization_partner_frs.md`
    *   `02_key_features/06_monetization_partner.md`
    *   `02_key_features/README.md`
    *   `03_user_types/01_customer.md`
    *   `03_user_types/02_provider_partner.md`
    *   `03_user_types/03_admin_internal_staff.md`
    *   `03_user_types/04_affiliate_partner.md`
    *   `03_user_types/05_data_analyst.md`
    *   `03_user_types/README.md`
    *   `06_security_access_considerations/01_authentication.md`
    *   `06_security_access_considerations/02_authorization.md`
    *   `06_security_access_considerations/03_data_protection.md`
    *   `06_security_access_considerations/04_session_management.md`
    *   `06_security_access_considerations/05_api_security.md`
    *   `06_security_access_considerations/06_internal_infra_security.md`
    *   `06_security_access_considerations/07_user_education.md`
    *   `06_security_access_considerations/README.md`
    *   `07_advanced_considerations/01_personalization_ai.md`
    *   `07_advanced_considerations/02_provider_integration.md`
    *   `07_advanced_considerations/03_data_governance.md`
    *   `07_advanced_considerations/04_operational_excellence.md`
    *   `07_advanced_considerations/05_legal_ethical_nuances.md`
    *   `07_advanced_considerations/06_innovation_future_proofing.md`
    *   `07_advanced_considerations/README.md`
    
    ## Accessing Detailed Information
    
    *   **Project Definition Document:**
        [Go to Project Definition Document (Main README)](./global_context/project_definition/README.md)
    
    *   **Development Guide:**
        [Go to Development Guide (Main README)](./global_context/development_guide/README.md)