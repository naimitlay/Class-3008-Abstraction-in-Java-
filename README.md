# Class-3008-Abstraction-in-Java-

Class 3008: Abstraction in Java (Part 1)  
=================================================================

MainActivity.java
==================================

package com.nxinaim.class3008;

import android.os.Bundle;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        TextView tvDesplay = findViewById(R.id.tvDesplay);
        tvDesplay.setText(""); // শুরুর ডিফল্ট টেক্সট ক্লিয়ার করার জন্য

        new FulltimeEmployee("Naim", "CEO", 1000, 2);



    }
}
===========================================================================================================================================================

Employee.java
============================
package com.nxinaim.class3008;

import android.util.Log;

public abstract class Employee {

    // গ্লোবাল ভ্যারিয়েবল (Instance Variables)
    private String name;
    private String position;
    private float salary;
    private int experience;

    public abstract float calculateTax();



    // ১ নম্বর কনস্ট্রাক্টর: এখানে প্যারামিটারের নাম এবং গ্লোবাল ভ্যারিয়েবলের নাম একই রাখা হয়েছে
    public Employee(String name, String position, float salary, int experience){
        // 'this.name' নির্দেশ করে উপরের গ্লোবাল ভ্যারিয়েবলকে
        // আর শুধু 'name' নির্দেশ করে এই কনস্ট্রাক্টরের প্যারামিটারকে
        this.name = name;
        this.position = position;
        this.salary = salary;
        this.experience = experience;
    }

   
    // Getter মেথডসমূহ
    public String getName() {
        return name;
    }

    public String getPosition() {
        return position;
    }

    public float getSalary() {
        return salary;
    }

    public int getExperience() {
        return experience;
    }
}
===================================================================================================================================

FulltimeEmployee.java
==================================
package com.nxinaim.class3008;

public class FulltimeEmployee extends Employee {


    public FulltimeEmployee(String name, String position, float salary, int experience) {
        super(name, position, salary, experience);
    }

    @Override
    public float calculateTax() {
        return getSalary() * 5/100;
    }
}

==========================================================================================

ParttimeEmployee.java
====================================
package com.nxinaim.class3008;

public class ParttimeEmployee {
}
