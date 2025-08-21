# creating-resources-using-functions-and-arrays
In DevOps scripting, arrays and functions are essential tools that make automation more efficient and maintainable. Arrays allow you to store and manage multiple values, such as server names or department buckets, and handle them dynamically with loops instead of repeating code. Functions, on the other hand, group commands into reusable, modular blocks that improve readability, reusability, and error handling in scripts. Together, they help automate cloud resource provisioning, deployments, and infrastructure management in a structured, scalable way—turning simple Bash scripts into powerful automation tools.


---

# 📝 Summary: Arrays & Functions in DevOps

## 🔹 Arrays

* **Definition**: An array is a variable that can hold multiple values under one name.
* **Usage in DevOps**: Arrays make it easy to manage **lists of resources** (e.g., EC2 instance types, S3 buckets, department names).
* **Benefits**:

  * Avoids repetitive code (loop through values instead).
  * Makes scripts **scalable** (add/remove items in one place).
  * Useful for **automation** (e.g., provisioning multiple resources).

**Example in DevOps:**

```bash
departments=("Marketing" "Sales" "HR")
for dept in "${departments[@]}"; do
  aws s3 mb s3://company-$dept-data
done
```

👉 Instead of writing 3 separate `aws s3 mb` commands, you loop once.

---

## 🔹 Functions

* **Definition**: A function groups commands into a reusable block of code.
* **Usage in DevOps**: Functions are like **mini-automation tools** inside your script.
* **Benefits**:

  * **Reusability** → Define once, call many times.
  * **Readability** → Break scripts into logical parts (`check_aws_cli`, `create_ec2_instances`).
  * **Error handling** → Functions can `return` codes to signal success/failure.

**Example in DevOps:**

```bash
create_ec2_instance() {
  aws ec2 run-instances --image-id ami-12345 --count 1 --instance-type t2.micro
  if [ $? -eq 0 ]; then
    echo "EC2 created!"
  else
    echo "Failed to create EC2."
  fi
}
```

👉 This encapsulates EC2 creation logic, making the script modular and easier to maintain.

---

## 🚀 Why They Matter in DevOps

* **Arrays**: Handle **multiple resources** efficiently.
* **Functions**: Encapsulate logic, enforce **modularity and reusability**.
* Together, they turn basic Bash scripts into **professional-grade automation tools** for tasks like:

  * Spinning up infrastructure (EC2, S3, VPCs).
  * Automating deployments.
  * Building reusable toolkits for cloud management.

---

✅ In short: **Arrays** = organize and scale resource lists.
**Functions** = structure, reuse, and modularize automation.
Both are **core scripting skills** that make you more effective in DevOps.

---

