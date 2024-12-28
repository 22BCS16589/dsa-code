#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
struct Policy {
    string name;
    string company;
    string type;
    double premium;
    double coverage;
    string description;
    string benefits;
};
vector<Policy> policies = {
    {"SecureLife", "LifeSecure Inc.", "Health", 3000, 500000, "Comprehensive health insurance.", "Covers critical illnesses, low premium, extensive network of hospitals."},
    {"SafeRide", "AutoProtect Co.", "Vehicle", 2500, 300000, "Affordable vehicle insurance.", "Covers damages, theft, and accidents with quick claim settlements."},
    {"HomeShield", "PropertyGuard Ltd.", "Home", 4000, 1000000, "Reliable home insurance.", "Covers natural disasters, burglary, and accidental damages."},
    {"EduSure", "FutureSecure Corp.", "Education", 2000, 200000, "Secure your children's future.", "Provides education fee coverage for unforeseen events."},
    {"HealthPrime", "MediCare Plus", "Health", 4500, 700000, "Premium health coverage.", "Includes annual health checkups and international coverage."},
    {"DriveCare", "RoadSafe Insure", "Vehicle", 2200, 250000, "Budget-friendly vehicle insurance.", "Covers third-party liabilities and personal accidents."},
    {"HomeGuard Pro", "SafetyFirst Homes", "Home", 3500, 800000, "Home insurance with extra benefits.", "Includes fire, flood, and appliance damage coverage."},
    {"StudyShield", "EducationPlus Inc.", "Education", 1800, 150000, "Education insurance with low premium.", "Covers tuition fees and extracurricular expenses."}
};
void displayPolicy(const Policy& policy) {
    cout << "Policy Name: " << policy.name << endl;
    cout << "Company: " << policy.company << endl;
    cout << "Type: " << policy.type << endl;
    cout << "Premium: $" << policy.premium << endl;
    cout << "Coverage: $" << policy.coverage << endl;
    cout << "Description: " << policy.description << endl;
    cout << "Benefits: " << policy.benefits << endl;
    cout << "------------------------------------" << endl;
}
void recommendPolicy() {
    string type;
    double maxPremium;
    cout << "Enter the type of insurance (Health, Vehicle, Home, Education): ";
    cin >> type;
    cout << "Enter your maximum budget for the premium: ";
    cin >> maxPremium;
    cout << "\nRecommended policies for " << type << " within your budget:\n";
    bool found = false;
    for (const auto& policy : policies) {
        if (policy.type == type && policy.premium <= maxPremium) {
            displayPolicy(policy);
            found = true;
        }
    }
    if (!found) {
        cout << "No policies match your preferences. Try increasing your budget or changing the type.\n";
    }
}
void comparePolicies() {
    string policy1, policy2;
    cout << "Enter the name of the first policy: ";
    cin.ignore();
    getline(cin, policy1);
    cout << "Enter the name of the second policy: ";
    getline(cin, policy2);
    Policy* p1 = nullptr;
    Policy* p2 = nullptr;
    for (auto& policy : policies) {
        if (policy.name == policy1) p1 = &policy;
        if (policy.name == policy2) p2 = &policy;
    }
    if (p1 && p2) {
        cout << "\nComparison between " << p1->name << " and " << p2->name << ":\n";
        cout << "Company: " << p1->company << " vs " << p2->company << endl;
        cout << "Type: " << p1->type << " vs " << p2->type << endl;
        cout << "Premium: $" << p1->premium << " vs $" << p2->premium << endl;
        cout << "Coverage: $" << p1->coverage << " vs $" << p2->coverage << endl;
        cout << "Benefits:\n" << p1->benefits << "\nvs\n" << p2->benefits << endl;
    } else {
        cout << "One or both policy names are invalid.\n";
    }
}
void aboutInsurance() {
    cout << "\nInsurance helps protect you from financial losses. Here's how:\n";
    cout << "- Health Insurance: Covers medical expenses for illnesses or injuries.\n";
    cout << "- Vehicle Insurance: Protects against accidents, theft, and damages.\n";
    cout << "- Home Insurance: Safeguards your property from disasters and theft.\n";
    cout << "- Education Insurance: Secures your child's education in unforeseen events.\n";
    cout << "Choose a policy that aligns with your needs and budget.\n";
}
void handleQuery() {
    cout << "Welcome to the Insurance Assistant Chatbot!" << endl;
    string choice;
    while (true) {
        cout << "\nHow can I assist you? Choose an option:" << endl;
        cout << "1. Get policy recommendations" << endl;
        cout << "2. Compare policies" << endl;
        cout << "3. Learn about insurance" << endl;
        cout << "4. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;
        if (choice == "1") {
            recommendPolicy();
        } else if (choice == "2") {
            comparePolicies();
        } else if (choice == "3") {
            aboutInsurance();
        } else if (choice == "4") {
            cout << "Thank you for using the Insurance Assistant. Goodbye!\n";
            break;
        } else {
            cout << "Invalid choice. Please try again.\n";
        }
    }
}
int main() {
    handleQuery();
    return 0;
}
